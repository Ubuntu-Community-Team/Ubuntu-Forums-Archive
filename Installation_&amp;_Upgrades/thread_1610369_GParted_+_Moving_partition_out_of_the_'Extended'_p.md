---
title: "GParted + Moving partition out of the 'Extended' partition"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by duberton on 2010-10-31
Hi guys!

Ive installed Windows 7 + XP + Ubuntu 10.10 and Mac Os X on my PC. The problem is that XP wont boot :/ Ive tried a lot of fixes for the last 2 days but still nothing. So ive come to conclusion that it might be probably due to its partition (dev/sda8) being inside of another Extended partition (dev/sda3) as you guys can see on the attachment. Is that the real problem? If so, how can i move it out of the extended partition. 

Thx in advance

---

### Post by sanderd17 on 2010-10-31
this shouldn't be the problem, btw, MAC OSX is inside an extended partition too. You might want to try the 

```

sudo update-grub

```

command to update your grub rules.

---

### Post by duberton on 2010-10-31
I already did it lots of times when i had lost grub2 because of the xp instalation or trying to sort things out :(

---

### Post by ajgreeny on 2010-10-31
That is the problem, I'm afraid; windows will refuse to boot from an extended partition and must have a primary partition, so you will need to install again, unless you can clone it or copy it some way to a new primary partition.

---

### Post by duberton on 2010-10-31
Alright man :D So, just to be sure, theres no way to move it? :(

thx for the reply guys!

---

### Post by ajgreeny on 2010-10-31
I don't think you can move it with gparted, but you may be able to with something like clonezilla, which is actually cloning and then restoring rather than moving the partition.

I have never used clonezilla so can't tell you any more, I'm afraid.

---

### Post by oldfred on 2010-10-31
While you cannot easily boot XP in the extended partition, you should be able to boot it from your other windows install. Windows combines boots into the one primary active (boot flag) partition. You may just need to update windows to find the XP install.

I have seen some advance users here make windows XP work. Not sure the details, but I saved some links:

Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

Boot WinXP from extended partition - Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Vista Win7 missing boot files meieifra
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

---

### Post by duberton on 2010-11-01
Alright guys, thx a lot! :D

---

### Post by srs5694 on 2010-11-01
There is another option, although it's messy and uses a flaky and dangerous hack: You can convert the disk to [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) form and then create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) for Windows, containing your three Windows partitions. Most modern OSes, including Linux, FreeBSD, and OS X, are quite happy to boot from a GPT disk, and they'll see GPT disks with hybrid MBRs as GPT disks. Windows, being the special needs student of the group, will see such a disk as an MBR disk and will use the MBR side of the partition table. You'll need to use a tool that's flexible enough to create a hybrid MBR containing precisely those partitions you need; some tools for this job just blindly take the first three GPT partitions and convert them to MBR partitions, but you'll need to select the correct partitions. [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) can do this, as can some versions of gptsync (but most versions of gptsync just convert the first three partitions). GPT fdisk can also do the lossless MBR-to-GPT conversion.

If you go this route, be aware that you'll have to re-install your boot loader. You may also need to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for use by GRUB. (You've definitely got room; the BIOS Boot Partition can be as small as about 35 or 40 KiB, and you've got at least 1.62 MiB free between [noparse]/dev/sda8[/noparse] and /dev/sda9.)

One other caveat: If you previously installed Windows on [noparse]/dev/sda8[/noparse] and somehow converted it to its present state, chances are it won't boot no matter what you do with it, at least not without some heavy-duty coaxing. Windows is very fussy about its boot partition, and its repair tools can seldom fix problems like changes in the partition's start sector, in my experience. Thus, you should count on re-installing Windows no matter what you do, at least if it's installed to [noparse]/dev/sda8.[/noparse] If it's installed on [noparse]/dev/sda2,[/noparse] OTOH, there shouldn't be a problem even now, since that's a primary partition.

---

### Post by duberton on 2010-11-02
> **oldfred said:**
> While you cannot easily boot XP in the extended partition, you should be able to boot it from your other windows install. Windows combines boots into the one primary active (boot flag) partition. You may just need to update windows to find the XP install.

I have seen some advance users here make windows XP work. Not sure the details, but I saved some links:

[B]Way to boot windows in extended logical partition with lilo's MBR
[http://ubuntuforums.org/showthread.php?t=1367323](http://ubuntuforums.org/showthread.php?t=1367323)[/B]
Major windows repair with dual boot and logical partition
[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)
You mean ntdetect and ntldr can't be on a logical partition, that is right. Yes the boot is via sda1. sda1 is there only for that purpose.
But it still needs a primary to boot from.
[http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition)

Boot WinXP from extended partition - Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Vista Win7 missing boot files meieifra
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

Got XP booting with the method/link in bold. But not entirely :( XP freezes in the loading screen. Ive tried once with the log info on and from what i remember it stopped reading at mup.sys or something :( What should i do now?

---

### Post by oldfred on 2010-11-02
Lilo works like the windows boot loader in that all it does is look for an active partition (boot flag) and jump to the code in the partition boot sector. Lilo does not care if it is a logical where windows does.

So you still must have some issue with the windows install in the partition. Some of the other links show how to configure boot.ini and recover the ntldr & ntdetect files to the windows root. You also have to have a valid NTFS boot sector.

---

### Post by duberton on 2010-11-03
Alright, solved!

THANKS A LOT FOR EVERYONE THAT POSTED HERE!

---

