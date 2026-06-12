---
title: "cannot get dual boot working."
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by samd21313 on 2014-04-27
I am a bit new at Linux (under 3 months), and not entirely sure where I am supposed to post this.
 I have been using Ubuntu 14.04, but have not been able to get into Windows 8. 
I ran boot-repair and got this url: ([http://paste.ubuntu.com/7347187](http://paste.ubuntu.com/7347187)). 
When I restarted, I am now able to log-in to Windows but am unable to boot into Ubuntu.
There is only grubrescue when I attempt to boot to Ubuntu. 
 
Also this message appears:
[COLOR=#000000]"You may want to retry after deactivating the [/COLOR][COLOR=#666666][[/COLOR][COLOR=#000000]Backup and rename Windows EFI files[/COLOR][COLOR=#666666]][/COLOR][COLOR=#000000] option.
[/COLOR][COLOR=#000000]The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode."
[/COLOR]
and not entirely sure how to fix that.

---

### Post by oldfred on 2014-04-27
It looks like you have installed Ubuntu in BIOS boot mode. And Windows is in UEFI boot mode. The two modes are not compatible, so you can only dual boot from UEFI menu. And you may have to turn on/off UEFI and/or turn on/off Legacy/CSM/BIOS boot modes in UEFI before booting in correct mode. Some auto switch.

You can boot Boot-Repair in UEFI mode and uninstall grub-pc (BIOS) and install grub-efi (UEFI) to convert your Ubuntu install.

But you need to turn off fast boot in Windows as that is always on hibernation first and as long as you dual boot keep it off. Windows on updates may turn it back on and reset itself to first in boot order.

From UEFI menu you still should be able to boot Windows in UEFI mode.
But if you have not fully backed up efi partition and Windows main install do so.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And make Repair flash drive as you cannot always get into Windows to fix itself and you cannot fix most Windows issues from Linux.
      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html

[/URL] Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
[/URL]

---

