---
title: "Windows 8.1 not booting after dual booting with ubuntu 14.04"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by Nikhil_Sahu on 2015-03-03
I had windows 8 preinstalled on my system with UEFI enabled. I installed ubuntu 14.04 by enabling legacy support and disbaling various parameters as mentioned on various forums.
Ubuntu installed successfully and after that i ran Recommended Repair from boot-repair and ran the commands that it poped up.
It gave a successful message and generated a log at [http://paste.ubuntu.com/10518416/](http://paste.ubuntu.com/10518416/) and asked to restart

After restarting it asked which of the options to boot from which is:

Ubuntu
Advanced Ubuntu
(2 more .efi options )
System Setup

System setup also sometimes fail saying errors "failed to load EFI"

---

### Post by ubfan1 on 2015-03-03
I was hoping that all you had to do was enable UEFI mode, since Windows needs to be in that mode to boot, but I see no Windows files at all on your boor-repair report.

---

### Post by oldfred on 2015-03-03
The two standard LVM installs both are full drive installs by default. One is the full drive encryption and the other just LVM. But both totally erase the entire hard drive.

LVM is not a standard partitioned install. It uses logical partitions inside the standard physical partitions.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

