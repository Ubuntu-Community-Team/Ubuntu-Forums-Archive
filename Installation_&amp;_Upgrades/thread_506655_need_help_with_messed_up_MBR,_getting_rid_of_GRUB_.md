---
title: "need help with messed up MBR, getting rid of GRUB and PartitionMagic errors (LBA/CHS)"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by kayzu on 2007-07-22
Okay, so what I planned to do was install Ubuntu on my PC and have it dual-boot with XP. Do I have to add that I messed it up? :p

Some info about my setup:
HDD1: 500gb (bought it a few days ago)
HDD2: 250gb (came with the PC, had Windows XP and a Recovery partition installed)

When I bought the new HDD, I installed XP on it, moved all my stuff from the old HDD to this one and wiped the XP Partition on the old HDD. Then I partitioned both HDDs like this:

HDD 1: (12gb) C: Windows XP (32-bit)
HDD 1: (150gb) D: Windows: Installed programs, my files
HDD 1: (200gb)  -- unallocated space --
HDD 1: (100gb) ext3 Partition, Ubuntu root
HDD 1: (5gb) Ubuntu swap partition

HDD 2: (6gb, FAT) F: original HP Recovery partition
HDD 2: (10gb) G: Pagefile XP
HDD 2: (100gb) E: Windows: Other stuff, downloads etc.

What I planned to do was to install Ubuntu on the HDD1 but NOT install GRUB to the MBR and use the NTLDR instead to boot Windows / Ubuntu via GRLDR or whatsoever (mainly because Windows will still be my main OS and I *might* uninstall Ubuntu/Linux in the future (but I doubt it :p))

After reading loads of stuff about GRUB and NTLDR and the MBR and how to install Ubuntu I decided to install it.  :)
I did back up the MBR of the HDD1 where I have Windows installed, but not the MBR of HDD1.
I booted from the Live CD and clicked on install. I created the ext3 and swap Partitions on HDD1 and I expected to see a Warning or something similar where I could tell GRUB NOT to install in my MBR and in root instead.
Seems like I missed it during the installation, so the install finished, the PC rebooted and I thought it would boot to Ubuntu again but it didn't, instead it booted to Windows XP.
I then booted from HDD2 and voila: GRUB.
Obviously, GRUB didn't write itself on the MBR of the disk where I installed Ubuntu and Windows but on the second HDD and left NTLDR on the other.

Okay, how do I remove GRUB from this MBR again without putting my Partitions at risk ? :-|

What scares me is that Norton PartitionMagic 8 now gives me an error message saying 
"Norton PartitionMagic has detected an error 116 on the partition starting at sector 25174862 on Disk 2.
The starting LBA value is 25174862 and the CHS value is 15483824.
The LBA and  CHS values must be equal.
Norton PartitionMagic has verified that the LBA value is correct and can fix the CHS value.
Would you like Norton PartitionMagic to fix this error?"

When I select No, PartitionMagic shows the complete Disk as 'Bad' although the Windows Partition manager shows the partitions and I can access all of them and boot to my Windows partition on that disk.

I have no idea what that means and don't know if I should let it fix it, after all I could lose all my data on that disk :-|

I hope you can help me, I'd really hate to uninstall Ubuntu again, I know it's a great OS once you get it working :p

---

### Post by kayzu on 2007-07-22
Sorry for the double post, but I thought for those who don't want to read the whole essay, I'll summarize it again (read my first post for more info):

I'm a Noob.
I have a PC with two HDDs, HDD1 has Windows and Ubuntu installed, HDD2 is just for Data and a bootable Recovery partition that came with my PC.
GRUB accidentally installed itself to the MBR of HDD2, which I didn't back up. (Thus, I can boot Windows normally when I boot from HDD1, and boot GRUB via HDD2)

How can I move GRUB from the MBS to the root partition of my Ubuntu install and how do I restore the MBR _without putting my partitions/my data at risk_? (Is the FIXMBR command safe to use?)
If that is fixed, how do I get NTLDR to boot Ubuntu?

And, maybe the most severe problem: Since I created the Ubuntu partitions via the Live CD and since GRUB installed itself to the MBR, Norton PartitionMagic 8.0 gives me this error when I start it up:
> Norton PartitionMagic has detected an error 116 on the partition starting at sector 25174862 on Disk 2.
The starting LBA value is 25174862 and the CHS value is 15483824.
The LBA and CHS values must be equal.
Norton PartitionMagic has verified that the LBA value is correct and can fix the CHS value.
Would you like Norton PartitionMagic to fix this error?
How do I fix this? Will letting Norton PartitionMagic fix this error put my partitions at risk?

---

### Post by kayzu on 2007-07-23
Okay, I formated the HDD where I had installed Ubuntu and Windows, reinstalled Windows, made the ext3/swap partitions for Ubuntu, booted to Ubuntu with the Live CD then backed up the MBR with

dd if=/dev/sdb of=mbr.backup bs=462 count=1

I installed Ubuntu to the partitions I created, then rebooted to Windows. PartitionMagic gave me the same errors about CHS/LBA values again but I didn't let it fix them but booted to Linux and restored the MBR with

dd if=mbr.backup of =/dev/sdb bs=1

After that, I booted to Windows again, changed the boot.ini, put GRLDR in C:\ and rebooted to GRUB
I tried to boot Ubuntu but it said there are errors in the partition table and didn't boot at all.

WHY? What am I doing wrong and.. why does nobody reply to this thread ???

Thanks, any help would be apreciated =/

---

