---
title: "Messed up partitions: &quot;Can't have a partition outside the disk warning&quot;"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by mnordal on 2011-12-19
Hi,

I have 10.04 installed and in an attempt to clean up and merge some partitions I of course messed it all up, ending with a Grub Rescue> prompt. Google'd a bit and got the grub restored and now it boots ok.

However, when I look at my partitions in Gparted or Disk Utility things looks weird. Especially in Gparted as it says my whole disk is "unallocated" (see screen shots). It also throws a "Can't have a partition outside the disk warning".
How can Disk Utility see my partitions and Gparted cannot?


I should mention that I used to have a dual boot (Ubuntu + WinXP) but that died with my partitioning mess-up. I'll probably re-install with Win7 once I get my partitions fixed up.

Disk Utility: 11 GB partition is Ubuntu, 141 GB "SYSTEM" is WINXP. 

Appreciate all help and suggestions you guys can give.

Thanks!

---

### Post by darkod on 2011-12-19
1. XP seems to be in a logical partition, it can't work from logical. Windows works from primary partitions, with few exceptions if you have more than one version of windows installed.

2. If you use Testdisk it can usually scan the disk and offer you to write the partitions found onto the partition table. Like that it would usually correct the errors in your partition table.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by mnordal on 2011-12-19
Thanks Darko. 

1.I only have one XP installed so I should change that logical partition into a primary you say? Tried that right now through Disk Utility but I don't see an option in Edit Partition how to make it primary. When clicking on the "Extended" partition above SYSTEM it says it's a logical container (can't change that either).


2. I used Testdisk actually and tried twice to write partitions that it had found. It didn't work and I felt like fumbling in blind so I thought I should stop before I messed it up more. TestDisk did mention though something about heads pr cylinder (or the other way around) being 255 and that they maybe should be 240. 

But why does Gparted not find partitions and what's with this error  "Can't have a partition outside the disk warning" ?

---

### Post by darkod on 2011-12-19
If there is an error in the partition table Gparted just shows the disk as unallocated. That is normal.

Try to see if fixparts can help recover the real partition table, and that program can also change logical partitions to primary. First see if it can only recognize the partitions correctly.

Later if you want to change the partition type, be careful to plan what the disk would look like after the change. The total of primary partitions is 4, and even if you have unallocated space you can't create any more partitions after that.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by mnordal on 2011-12-19
Ok thanks, will take a look at the fixparts and see if that might help. 

Just noticed in Disk Util that the 5.9 GB (to be) Swap space is flagged as bootable whereas my actual Linux partition (11 GB Ext4) is not flagged bootable. Does this mean that grub or MBR is located on the SWAP disk now?

---

### Post by darkod on 2011-12-19
No, the boot flag doesn't show where the bootloader is. Thw windows boot process depends on the boot flag, it needs to be where the boot files are, usually the windows partition. But with win7 you can have the boot files on separate partition.

For the ubuntu boot process it doesn't matter where the boot flag is.

---

### Post by mnordal on 2011-12-19
Yes! Got it fixed - thanks a lot Darko!

I could see in fixparts as well that there was a section overlap betweentwo partitions, so I used "omit" to get rid of the SWAP partition. Saved and rebooted and Gparted and Disk Util now shows healthy partitions :o)

Still can't boot windows but I think this should be fixed when I re-install Win 7, right? Or will Windows take over my boot/MBR/grub and shut me out of Ubuntu?

---

### Post by darkod on 2011-12-19
1. Yes, installing windows will delete grub from the MBR but restoring it is easy. Just have the ubuntu cd at hand.

2. Before installing win7 you will have to prepare a primary ntfs partition with the boot flag on it. You better prepare it with Gparted because that way you avoid the win7 installer creating the small system reserved partition (you are short on primary partitions).
If a ntfs partition is prepared in advance the installer doesn't create the system reserved.

PS. You need the boot flag to be set on that partition because windows automatically puts boot files where the flag is.

---

### Post by mnordal on 2011-12-19
Ok, will follow that procedure..

Thanks again for your excellent advice Darko!

---

