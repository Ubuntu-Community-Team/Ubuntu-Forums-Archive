---
title: "Windows 10 not booting up after installing Ubuntu"
date: 2022-01-30
forum: Installation &amp; Upgrades
---

### Post by giggs14 on 2022-01-30
HI,

I recently installed Ubuntu for dual boot along with Windows 10. Windows 10 is on sd1. Now when select the option of booting into Windows 10, a black screen comes up and bringing up the option screen again. I already tried updating grub and it says that windows 10 found on /dev/sda1, but it doesn't boot into windows.
Here is my boot-repair log. Would be glad if someone can help. Thanks!!
[URL="https://paste.ubuntu.com/p/SRP5WprJYJ/"]https://paste.ubuntu.com/p/SRP5WprJYJ/

[https://ibb.co/6gYDC1H](https://ibb.co/6gYDC1H) [/URL]

---

### Post by oldfred on 2022-01-30
See lines 11 & 12.
You broke Windows by attempting to install grub to a Windows NTFS partition.
Whether UEFI or BIOS, you specify a drive like sda or sdb to install grub, not a partition like sda1.

NTFS does keep a backup of the PBR partition boot record or BS boot sector (both names used).
Windows has to have its info in the BS.
Testdisk and many Windows tools can restore the backup BS if not otherwise damaged.
It may say grub in BS is valid as technically
 you can install it to BS, but never with NTFS.

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

If both drives are internal you may want to install grub to MBR of sdb and keep Windows boot loader in MBR of Windows drive.
Grub only boots working Windows, so you sometimes have to directly boot Windows. Much easier with UEFI, but with two drives you have two MBR, so can have both BIOS boot loaders on system.

Since UEFI based system, better to have Windows & Ubuntu in UEFI boot mode on gpt partitioned drives. But conversion from MBR to gpt normally erases a drive, so major conversion requiring good backups of data & reinstall of systems. More for longer term planning.

Windows only boots in UEFI mode from gpt. And not easy to convert, best to plan new install.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by giggs14 on 2022-01-31
Thanks for the reply. I was following [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

After following #6 in step 3, I can’t see that “Boot sector” info…instead I see something like below.

#5 in step 3:
[https://ibb.co/ydgVHkV](https://ibb.co/ydgVHkV)

#6 in step 3 ( no boot sector info):
[https://ibb.co/CmySCMH](https://ibb.co/CmySCMH)

How can I get that boot sector info?
Thanks.

---

### Post by oldfred on 2022-01-31
Looks like you are in file recovery, not at choosing the partition.
You want the sda2 partition. 
Not sure what screens you get. I have not used MBR for 10 years and do not have a  system with MBR partitions.
With my gpt I get different screens.

---

