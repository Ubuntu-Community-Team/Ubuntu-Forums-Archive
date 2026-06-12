---
title: "Installing bootloader to a CD"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by demonguard on 2007-10-19
I have a problem. I would love to install Ubuntu dual boot (and have before) except the GRUB/LILO menu bugs the hell out of everyone else that uses this computer. So I was wondering if it would be possible to do a HD install, but not install a bootloader. And then burn GRUB (or lilo) to a disk. So that windows would start if I didn't have the disk in, but when I put it in and restarted it would give me a menu to select XP or linux.

---

### Post by logos34 on 2007-10-19
To make a Grub Boot CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD](http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD)
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

Or use [Super Grub Disk.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by rsambuca on 2007-10-19
It is probably a lot easier just to install grub, but set it to default to Windows for everyone else, and you can set the timeout to 1 or 2 seconds, and also hide the grub menu.  No one will even no it exists.  The one or 2 seconds is plenty of time for you to press escape and enter the grub menu to select Ubuntu.

---

### Post by logos34 on 2007-10-20
demonguard,

I didn't really read your question.  Rsmbuca's right--the available options in menu.lst should should be sufficient for your purposes.  

[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

