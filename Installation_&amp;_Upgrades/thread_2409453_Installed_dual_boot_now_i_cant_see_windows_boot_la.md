---
title: "Installed dual boot now i cant see windows boot later"
date: 2019-01-02
forum: Installation &amp; Upgrades
---

### Post by bhanu904 on 2019-01-02
I tried installing ubuntu dual boot ... not along side window .... While installing grub it showed some error and finally i got error as grub efi signed error something....

Noew i cant even see Windows boot loader on OS manager in BIOS..

I tried boot repair using boot repair tool in live ubuntu

this is summary please help

[https://pastebin.com/raw/VMgnjZTj](https://pastebin.com/raw/VMgnjZTj)

---

### Post by oldfred on 2019-01-02
It looks like you have newer UEFI hardware, but both Windows & Ubuntu installed in BIOS boot mode to MBR partitioned drive. If you tried UEFI install, grub fails with no ESP - efi system partition.
But when you rebooted installer to run Boot-Repair, you booted in UEFI boot mode. You only want BIOS boot mode. Boot Selection with USB drive is independent of default boot of internal drives.

You must be consistent with new systems, always BIOS/Legacy/CSM or always UEFI for both Windows & Ubuntu and both installers & once installed.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch.


Windows 8 or 10 is not as dual boot friendly in BIOS mode as in UEFI boot mode. Microsoft required vendors with Windows 8 or later to only install in UEFI boot mode to gpt partitioned drives.

Grub only boots working Windows which means Windows fast start up/hibernation must be off, but Windows turns it back on with updates. Or if Windows gets corrupted and needs chkdsk, grub will not boot it. Best to then have a Windows repair/recovery flash drive to make repairs.
And you have to temporarily install Windows BIOS boot loader, fix Windows, and restore grub boot loader. With UEFI, you just choose Windows in UEFI to directly boot it and use internal repair console or change settings.

Boot Windows and make sure Windows fast start up is off. And make repair flash drive. And if you have not made full backup of Windows do that also.
Then reboot Ubuntu live installer in BIOS/CSM/Legacy mode and install grub using Boot-Repair in BIOS mode to MBR of sda drive.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by bhanu904 on 2019-01-03
> **oldfred said:**
> It looks like you have newer UEFI hardware, but both Windows & Ubuntu installed in BIOS boot mode to MBR partitioned drive. If you tried UEFI install, grub fails with no ESP - efi system partition.
But when you rebooted installer to run Boot-Repair, you booted in UEFI boot mode. You only want BIOS boot mode. Boot Selection with USB drive is independent of default boot of internal drives.

You must be consistent with new systems, always BIOS/Legacy/CSM or always UEFI for both Windows & Ubuntu and both installers & once installed.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch.


Windows 8 or 10 is not as dual boot friendly in BIOS mode as in UEFI boot mode. Microsoft required vendors with Windows 8 or later to only install in UEFI boot mode to gpt partitioned drives.

Grub only boots working Windows which means Windows fast start up/hibernation must be off, but Windows turns it back on with updates. Or if Windows gets corrupted and needs chkdsk, grub will not boot it. Best to then have a Windows repair/recovery flash drive to make repairs.
And you have to temporarily install Windows BIOS boot loader, fix Windows, and restore grub boot loader. With UEFI, you just choose Windows in UEFI to directly boot it and use internal repair console or change settings.

Boot Windows and make sure Windows fast start up is off. And make repair flash drive. And if you have not made full backup of Windows do that also.
Then reboot Ubuntu live installer in BIOS/CSM/Legacy mode and install grub using Boot-Repair in BIOS mode to MBR of sda drive.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]


Now I don't see anything.... Either windows or Ubuntu.... Can you please tell me the starting steps... I am very new to this

---

### Post by oldfred on 2019-01-03
Use your  Windows repair flash drive and fix Windows. Then make sure fast start up is off.

---

