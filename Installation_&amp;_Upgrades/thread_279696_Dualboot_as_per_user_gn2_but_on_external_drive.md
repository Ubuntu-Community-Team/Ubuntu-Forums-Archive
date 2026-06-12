---
title: "Dualboot as per user gn2 but on external drive"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by plantbreeder on 2006-10-18
I'll preface this by saying that I am a raw recruit in the world of Linux.  I decided to try ubuntu x64 and read through the forums about doing a dual boot installation.  I decided to go the route suggested by gn2, and install ubuntu by disconnecting the primary harddrive to circumvent supposed issues with GRUB.  My second harddrive is an external drive that I use for storing my work, and I got ubuntu to install on it after some partioning fears.  Here's the problem: as long as the primary harddrive is unplugged, ubuntu will load fine; but when I plug in the primary, select the "ubuntu" harddrive in the boot menu, something fails.  I get the following message

Booting kernel
[   36.116997] i8042.c: can't read CTR while initializing i8042.
ALERT! /dev/sde2 does not exist.  Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
#

  I looked for someone who had done an install on a usb drive, but didn't find anything useful.  Any help would be greatly appreciated.

---

### Post by gn2 on 2006-10-18
> **plantbreeder said:**
> I'll preface this by saying that I am a raw recruit in the world of Linux.  I decided to try ubuntu x64 and read through the forums about doing a dual boot installation.  I decided to go the route suggested by gn2, and install ubuntu by disconnecting the primary harddrive to circumvent supposed issues with GRUB.  My second harddrive is an external drive that I use for storing my work, and I got ubuntu to install on it after some partioning fears.  Here's the problem: as long as the primary harddrive is unplugged, ubuntu will load fine; but when I plug in the primary, select the "ubuntu" harddrive in the boot menu, something fails.  I get the following message

Booting kernel
[   36.116997] i8042.c: can't read CTR while initializing i8042.
ALERT! /dev/sde2 does not exist.  Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
#

  I looked for someone who had done an install on a usb drive, but didn't find anything useful.  Any help would be greatly appreciated.

PCLinuxOS is the best bet for your needs, it has a GUI installer to install directly to USB.

There Is no easy way to achieve this with Ubuntu that I have found.

PCLinuxOS is in my opinion a far better distro than Ubuntu.

---

