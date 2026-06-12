---
title: "Grub installed and windows 10 will not boot"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by dlg612 on 2020-03-31
I moved two hard drives to a new motherboard.  One drive already had Windows 10 installed.  On the other blank drive, I installed ubuntu 18.04.4.   Grub appears to have overwritten the windows 10 drive's boot area.  The Grub menu appears no matter which drive I select with BIOS.  Windows is a grub menu item but when selected windows goes into a repair/diagnostic loop.  I have run boot-repair from a live ubuntu cd.  No fix, just another windows menu item created in grub.  Here is the URL from boot-info     	 	 	 	   [http://paste.ubuntu.com/p/5hGry9hb4D/](http://paste.ubuntu.com/p/5hGry9hb4D/)

I have no means to reinstall windows 10.  
I prefer to select the OS through the BIOS hard drive selection at startup, as I did with the previous motherboard..

---

### Post by oldfred on 2020-03-31
With multiple drives and different installs you do not what the auto fix from Boot-Repair. Only use the advanced options.
With BIOS mode, it can install a Windows type boot loader to sdb, or use your Windows repair flash drive to fixMBR.
> The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBRs of all disks
Choose second drive's MBR and Windows partition. It should see Windows and offer to install syslinux.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Grub will only boot Windows 10 if Windows fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

