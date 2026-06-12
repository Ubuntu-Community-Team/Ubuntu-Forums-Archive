---
title: "Ubuntu ubi-partman crashed with exit code 141"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by rschanzenbacher on 2013-11-19
When I try to install ubuntu 13.04 the installer crashes and says ubi-partman crashed with exit code 141.  I know this is an old glitch in ubuntu 10.10 but its happening to me. :(
Please tell me how to fix it and I will give you thins popcorn :popcorn:.  The OSes i have installed are just windows 8.1 and the partitons are just my data and os and recovery.  I use no updates or third party software while installing.


Any help is appreciated.

---

### Post by oldfred on 2013-11-20
post this from live installer.

 sudo parted /dev/sda unit s print

Are you using manual install or Something else or one of the auto install options?
Did you turn hibernation off in Windows 8?
If still hibernated the installer cannot see the NTFS partition to know about it.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

