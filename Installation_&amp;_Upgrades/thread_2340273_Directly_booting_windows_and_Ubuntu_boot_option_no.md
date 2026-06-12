---
title: "Directly booting windows and Ubuntu boot option not showing"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by avijit6399 on 2016-10-17
[http://paste2.org/GmtBB8Jn](http://paste2.org/GmtBB8Jn)

---

### Post by oldfred on 2016-10-17
You have BIOS/MBR configuration which only boots from MBR or first sector on drive.
You still have Windows boot loader in MBR, so cannot boot Ubuntu.
And you installed grub to a partition which normally is not done, and installed it to a Windows formatted partition which cannot ever be done.

First make Windows repair/recovery drive. Boot-Repair can only do very minor fixes to Windows.
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[http://www.digitalcitizen.life/create-usb-memory-stick-system-recovery-tools](http://www.digitalcitizen.life/create-usb-memory-stick-system-recovery-tools)

In Windows turn off fast start up or always on hibernation:
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) 
    
Let Boot-Repair run its default fix to install grub to MBR.

Then see if you can repair sda1. It may have backup partition boot sector like NTFS does, not sure.
This shows NTFS, but may work for FAT32, your sda1
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

