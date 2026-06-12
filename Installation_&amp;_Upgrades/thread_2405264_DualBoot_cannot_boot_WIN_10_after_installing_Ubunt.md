---
title: "DualBoot cannot boot WIN 10 after installing Ubuntu"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by gitlukaszk on 2018-11-03
Hello,

Please help me fix the issue, can't boot WIN 10 after installing Ubuntu.
After clicking WIN 10 boot in Grub it's just going back to main window.

link: [http://paste.ubuntu.com/p/bbf5WBVyT9/](http://paste.ubuntu.com/p/bbf5WBVyT9/)

Thanks in advance

---

### Post by oldfred on 2018-11-03
You almost never install grub to partition with BIOS boot. And never ever install grub to BS - boot sector or PBR partition boot record of a NTFS partition.
But NTFS does keep a backup which you may be able to restore. Testdisk may say grub is valid as it can be, but never is in NTFS.

      ```
 sda1: ______________________________
   File system:       [COLOR=#ff0000]ntfs[/COLOR]

 Boot sector type: [COLOR=#ff0000] Grub2 [/COLOR](v1.99-2.00)
Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1  

     and looks at sector 607803856 of the same hard drive 
   for core.img. core.img is at this location and looks 
   for (,msdos5)/boot/grub. It also embeds following 
   components: 


```     

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Then run:
sudo update-grub

Windows 10 with its fast start up and its auto update that turns it back on, make it difficult to dual boot in BIOS mode.
Grub only boots working Windows. Or Windows that is not hibernated which is fast start up, nor needs chkdsk. 
So you may need to temporarily restore a Windows boot loader to MBR, boot Windows, fix Windows & restore grub to MBR.
Also have a Windows repair/recovery flash drive for Windows fixes and Ubuntu live installer for Ubuntu fixes.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

All systems in last 5 years are UEFI.
And from UEFI, you can always directly boot Windows when it has issues, but still should have Windows repair disk.

---

