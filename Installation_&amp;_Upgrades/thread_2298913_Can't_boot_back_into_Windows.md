---
title: "Can't boot back into Windows"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by steve226 on 2015-10-14
Hi guys.

I'm sure you've seen this a thousand times so apologies in advance.

Just installed the latest version of Ubuntu and now I can't boot back into Windows. I created a separate partition for the root but for some reason I think it's been installed on my C Drive. I tried doing a boot repair but keep on getting an error message, here is the result:

[http://paste.ubuntu.com/12783468/](http://paste.ubuntu.com/12783468/)

I can still see all my Windows files/folders in Ubuntu so I don't think I've overwritten the C Drive, just somehow can't boot back into Windows.

Pulling my hair out so any help I'd really appreciate it.

Thanks.

---

### Post by yancek on 2015-10-14
You have some wubi files on the windows partition.  At the end of the boot repair output there is a link to a site which explains how to get rid of that.  Wubi doesn't work with new windows versions and is also not being developed/supported any longer.  Did you do this at some time in the past?  In any case, the first step you should take is to get rid of the wubi files.  You also have a Linux/Ubuntu partition on sda4 but you have windows code in the master boot record of the drive.  A default windows will not boot Linux.  You would need to manually create a file needed and then manually edit the windows boot file.  It would probably be simpler to use the boot repair option and install Grub to the MBR of the drive.  The grub.cfg file (which is the boot menu) already has a correct entry for Ubuntu and windows.

I notice you have Grub files on the first partition, sda1 which is a windows partition.  That's usually not good but it might have something to do with wubi.  Never used wubi myself so don't know what you should expect.

FYI:  The default in the installation is to install the Ubuntu Grub boot code to the MBR of the first drive so you would have had to have changed that during the installation.  Either that or something just went wrong.  You do have an option if you use the manual (Something Else) installation option.

---

### Post by oldfred on 2015-10-14
Windows has essential boot info file name & partition size amoung others in the partition boot sector (PBR). So when you installed grub to sda1 or the NTFS boot partition you broke Windows. NTFS does keep a backup which usually you can use to restore it.  Testdisk may say grub is valid in PBR, which it can be, but never recommended, but it still is wrong and you want to restore backup if valid. 
If not you need a Windows repair flash drive to create a new PBR.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by steve226 on 2015-10-15
> **oldfred said:**
> Windows has essential boot info file name & partition size amoung others in the partition boot sector (PBR). So when you installed grub to sda1 or the NTFS boot partition you broke Windows. NTFS does keep a backup which usually you can use to restore it.  Testdisk may say grub is valid in PBR, which it can be, but never recommended, but it still is wrong and you want to restore backup if valid. 
If not you need a Windows repair flash drive to create a new PBR.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

Hi oldfred,

When I run the TestDisk thing in the Terminal, when clicking on the Windows partition I don't have an option to BackupBS, only RebuildBS and RepairMFT.

The option is available when on the "System Reserved" partition of the drive?

When I click on "RebuildBS" on the Windows partition it doesn't do anything, just gives me more options. I can rebuild the one with sda5 partition.

Some screenshots:

[http://imgur.com/x6dWCuo](http://imgur.com/x6dWCuo)

[http://imgur.com/I2jmxB5](http://imgur.com/I2jmxB5) -**I'm pretty sure this is the Windows partition**

[http://imgur.com/goqWaHJ](http://imgur.com/goqWaHJ)

---

### Post by oldfred on 2015-10-15
If the backup is identical and you still have grub in the PBR, then you installed grub more than once to the NTFS PBR.

You do need to run the rebuildBS on the sda1 or system reserved partition. Not sure why testdisk would not give that option. I do not think any Windows repairs will recognize the partition as your boot partition with grub in it. Windows looks as PBR and needs to see a NTFS signature.

The rebuildBS, I believe still creates an XP type, structure is somewhat different than newer NTFS. In the PBR is which boot loader to use and XP has ntldr and Vista or later has bootmgr. Usually chkdsk from a newer Windows repair disk will update the PBR to be correct. I ran a chkdsk from a Windows 7 repair disk on my XP years ago. It made more fixes than the chkdsk from XP, but converted the PBR to Windows 7. I had to run a XP chkdsk to fix it. Testdisk showed me the details of the differences, but the boot file name was all that was easily read.

From a Windows repair disk you can also run this:
 Really using bootsect.exe to restore partition boot sector - PBR

 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Bootsect.exe updates the master boot code (BS) for hard disk partitions
in order to switch between BOOTMGR and NTLDR.
You can use this tool to restore the Boot_Sector (BS) on your computer.

If none of that works move boot flag from sda1 to sda2, and copy bootmgr & /boot which has the BCD into sda2.

---

