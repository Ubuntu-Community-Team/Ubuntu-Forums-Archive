---
title: "Installed Ubuntu 16.04 and Windows 10 doesn't work"
date: 2016-07-08
forum: Installation &amp; Upgrades
---

### Post by dankonig on 2016-07-08
Installed Ubuntu 16.04 as a dual boot with Win  10. I resized the  partition for Ubuntu to 50GB. I did not accept  installing using UEFI.  Once Ubuntu was installed I rebooted but no  Windows 10 option. I tried  uninstalling and reinstalling twice. No luck.  I then booted from the  USB into "Try Ubuntu" and downloaded and ran the  OS Unistaller.  Uninstalled Ubuntu but I get an error screen on reboot. Something about  grub. No luck  booting into Windows.


 Not sure if  this is relevant but when I try and access one of the  windows drives to copy the data out of there in Ubuntu(labelled Win8) I  get this error.


 Error mounting /dev/sda1 at /media/ubuntu/Win8: Command-line `mount -t  "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda1"  "/media/ubuntu/Win8"' exited with non-zero exit status 14: Windows is  hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I can access the other drives where the programs reside. Can't find the desktop files though.

---

### Post by yancek on 2016-07-08
Did you install windows 10 yourself NOT in UEFI mode?  If it was pre-installed then in all likelihood, it was UEFI and Ubuntu would then need to be UEFI or you will get the result you have.  Some info on this at the Ubuntu documentation site below on UEFI.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The error message you posted means that you failed to shut down windows fully before trying to access it from Ubuntu.  If you can't boot windows because of an improper bootloader installation, you can mount the windows partition with the ro (read-only) option.  You might find it easier to reinstall Ubuntu UEFI if that is what you use with windows.  It is explained at the link above.

---

### Post by oldfred on 2016-07-08
You need to have Windows fast start up off and install in UEFI boot mode as yancek suggests above:

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch. Or from grub can only boot another system installed in same boot mode.
You may still be able to boot from UEFI boot menu or UEFI one time boot key like f10 or f12.

---

