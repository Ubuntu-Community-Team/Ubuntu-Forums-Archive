---
title: "Installation in parallel to Windows 10 don't work"
date: 2018-09-23
forum: Installation &amp; Upgrades
---

### Post by guenny2804 on 2018-09-23
Hi,

i try to install Ubuntu 18.04. in parallel to Win10 for the first time. I followed some guide online but the installation stopped / crashed with a GRUP Boot Loader install issue. 
I managed to get the boot information via Ubuntu Live System - but i cannot identify the issue or the setting I may have to change.

Boot Info ist here: [http://paste.ubuntu.com/p/4bc6s6wGpx/](http://paste.ubuntu.com/p/4bc6s6wGpx/)

HW Config and the Rufus Settings:

[ATTACH=CONFIG]281167[/ATTACH][ATTACH=CONFIG]281168[/ATTACH][ATTACH=CONFIG]281169[/ATTACH]

What do I need to Change?

rgds
Sebastian

---

### Post by ajgreeny on 2018-09-23
You do not seem to have a small (200 - 500MB) ESP/EFI partition formatted to fat32 with the boot flag added.

Windows 10 will normally be installed using UEFI if it was an OEM install, but your disk is formatted as ms-dos or the old legacy manner so Win 10 must be installed in BIOS mode, not UEFI.

Did you install Windows 10 or was it an OEM install, and when you installed Ubuntu did you use UEFI to boot the install medium or legacy BIOS?
Both OSs must be installed in the same mode for a useful dual boot system, though it may be possible in some cases to boot either OS by pressing a key at power-on to set the boot device.

Hopefully a colleague who has much more knowledge than me at reading the boot-info output will appear here and be able to help you more, but I believe your problem is related to tis UEFI/BIOS inconsistency.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for more details of UEFI vs BIOS.

---

### Post by oldfred on 2018-09-23
Windows 10 can be installed in the now 35 year old BIOS boot mode on MBR partitioned drives. It just makes it a bit more difficult with BIOS.
Windows has fast start up which is really just hibernation as Windows boots so slow. And Windows will turn it back on with updates. 
But grub will not boot hibernated Windows. So then you have to temporarily reinstall a Windows boot loader, fix Windows, and then restore grub boot loader. With newer hardware for the newer Windows in UEFI boot mode, you can just choose which to boot at any time from UEFI menu.

Boot-Repair says hibernation is on.

> the disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

While in Windows make a Windows repair/recovery flash drive. And keep your Ubuntu live installer to reinstall grub when needed.

Boot Windows and turn off Windows fast start up. Then use Boot-Repair to install grub2's boot loader to MBR of your drive.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[URL="http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions"]http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions

      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions"]
[/URL]

---

### Post by guenny2804 on 2018-10-14
Hi Both,

thanks for your help. I decided to install Win10 from scratch with UEFI. Now it works with Ubuntu and Win10 in parallel. 

rgds
Sebastian

---

