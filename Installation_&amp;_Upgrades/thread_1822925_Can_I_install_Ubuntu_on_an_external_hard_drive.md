---
title: "Can I install Ubuntu on an external hard drive?"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by Webnix on 2011-08-11
Hi I Thought that I would try to install Ubuntu 11.04 on to a external hdd coz Mine is 1.5tb. and every time I try to install Ubuntu with Wubi it crashes. It goes to a screen like Command. and I know my system can but from a USB coz I already tested it and it detects laptop Hdd and CD and Usb drive as a chose to boot from. I am on a Windows 7 HP G72-251NR Notebook PC With 2.3ghz dual core Pentium 3 gigs of Ram 64x bit System

---

### Post by dino99 on 2011-08-11
yes of course (if your bios find and recognize it and accept to boot on it)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by TheGuvernor on 2011-08-11
Do you have Ubuntu burned to a CD/DVD? If so boot into your BIOS, set your CD/DVD ROM drive as first in the boot sequence. Then make sure your external drive is showing. If so restart with the copy of Ubuntu in your CD/DVD Rom tray and it should go from there. During the install make sure you choose the external drive.

---

### Post by YesWeCan on 2011-08-11
Make sure the boot loader (Grub) is installed to the external disk too. If you don't see how to set this then do not install - come back here for help.

Unfortunately, the installer defaults to putting Grub on your sda disk, which is probably your internal HD. If it does this you won't be able to boot anything at all unless your external disk is connected, which is a real PITA.

---

