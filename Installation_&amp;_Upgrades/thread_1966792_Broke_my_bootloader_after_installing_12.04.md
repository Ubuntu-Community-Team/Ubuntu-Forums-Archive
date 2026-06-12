---
title: "Broke my bootloader after installing 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Karunamon on 2012-04-27
I just installed Ubuntu 12.04 and I think I selected the wrong partition to install the boot loader on to.

Prior to install, my partition map was:

```
1: NTFS (Reserved, Windows 8 Boot Manager)
2: NTFS (Windows 7 NTFS)
3: Extended
 4: Linux Swap (From a previous Linux install)
 5: NTFS (Windows 8)

```

My idea was to toss the Windows 8 partition and install there. My problem came in when I chose to install the boot loader onto Partition 1.

Grub correctly identifies 1 as a Windows 8 loader, however, attempting to boot this (via the usual root, chainloader+1) just leads to the Grub menu coming up again and again.

I'm not sure how to break out of this loop. I can't directly boot partition 2 either, that gives me an "Invalid Signature" error from Grub.


(Aside: Am I the only person that thinks Grub2 is a right pain in the **** compared to the last version?)

---

### Post by oldfred on 2012-04-27
Grub2 is not normally installed to a partition.

But your issue is with Microsoft. All NTFS partition have to have a NTFS signature with includes info on the partition size (same as partition table) and if bootable which boot loader (bootmgr or ntldr for XP) to use.

You may be able to repair NTFS partition as it does keep a backup. If you installed more than once then you will have to use a Windows repairCD or USB to fix the partition boot sector.
You have to have boot flag on NTFS partition that you want to repair if using Windows to repair it.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Then you will need to install the grub2 boot loader to the MBR of the drive not a partition.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.
[https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool](https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool)

---

### Post by Karunamon on 2012-04-27
> **oldfred said:**
> This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.


This is exactly what I needed! I wasn't even aware that a backup copy of the boot sector is kept.. learn something new every day :)

Thanks!!

---

