---
title: "Install not asking location for grub bootloader"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by temis01 on 2007-10-19
I am used to test ubuntu alternate test CDs from cdimage.com

When I installed gutsy, the installer will ask where to install grub bootloader.

Since early october the installer will not ask where to install grub and automatically install to the first HDD known in fdisk -l

Is there a way to force the installer to ask where to install grub during install (kernel option before install / bios HDD order / else ...) ?

1st HD = vista
...
4th HD = gutsy

thanks
temis

---

### Post by staticsage on 2007-12-19
I just ran into this problem. I'm using a nonstandard bootloader, so the alternate cd installer wrote grub to the MBR without me confirming. Is there any way around this?

---

