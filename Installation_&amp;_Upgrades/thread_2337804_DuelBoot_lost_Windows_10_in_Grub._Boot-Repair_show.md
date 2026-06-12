---
title: "DuelBoot lost Windows 10 in Grub. Boot-Repair shows the windows partition still there"
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by corky7tx2 on 2016-09-21
After installing Ubuntu for DuelBoot lost Windows 10 in Grub. Boot-Repair shows the windows partition still there?

Here is the file [http://paste2.org/WPK9dbed](http://paste2.org/WPK9dbed) from Boot-Repair. Thanks for any suggestions


[LIST=1]
[*]sda2: __________________________________________________________________________

[*]


[*]    File system:       

[*]    Boot sector type:  Unknown

[*]    Boot sector info: 

[*]    Mounting failed:   mount: unknown filesystem type ''

[*]mount: unknown filesystem type ''

[*]


 
[/LIST]

---

### Post by oldfred on 2016-09-21
Did you turn Windows fast start up or always on hibernation off?
Did you use Windows to resize the NTFS partition with Windows and immediately reboot, so it can run chkdsk.

Linux NTFS driver only mounts and boots working Windows or Windows that is not hibernated, nor needs chkdsk.

Best to use your Windows 10 repair/recovery drive to fix Windows.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 


You may be able to use Boot-Repair to restore a generic Windows MBR and boot into Windows own recovery mode using f8.
After Windows is fixed restore grub2's boot loader with Boot-Repair.

---

### Post by corky7tx2 on 2016-09-21
Yes Windows fast startup and Hibernation is off

Yes I used windows to resize the NTFS partition and was able to boot both Windows and Ubuntu. The last time I rebooted it cam up with no operating system available. I then used a Ubuntu CD and ran Boot-Repair and now Ubuntu is working. Just don't have the Windows option.

Here is the file [[COLOR=#dd4814]http://paste2.org/WPK9dbed[/COLOR]]("http://paste2.org/WPK9dbed") from Boot-Repair. Thanks for any suggestions

Windows 10 was on sda2

---

### Post by corky7tx2 on 2016-09-21
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda2 : Error code 12
mount -r /dev/sda2 /mnt/boot-sav/sda2
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda2 : Error code 12

---

### Post by oldfred on 2016-09-21
Those are typical errors in Windows.
And you probably need to boot your Windows repair disk and run chkdsk and make double sure you have fast start up off.

---

### Post by corky7tx2 on 2016-09-22
This is the error I receive with chkdsk

[FONT=Courier New]chkdsk can not be run on the drive
 The type of the file system is RAW.
 CHKDSK is not available for RAW drives.[/FONT]

---

### Post by oldfred on 2016-09-22
RAW means there is no NTFS signature at all. Or you installed grub to the Windows partition's boot sector.

You can see if you can restore backup BS, or install a generic (I think it is XP type) NTFS BS, but then chkdsk will run and convert it to the newer type.
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

---

