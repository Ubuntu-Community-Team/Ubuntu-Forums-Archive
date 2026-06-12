---
title: "HELP-DualBoot-Win7 Unusable"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by jcbaird on 2012-09-15
I have an Alienware m17x R1 computer with dual Nvidia geforce 260m graphics cards and 1 Nvideo 9400, 16GB Ram, 1 750GB drive (Drive C) and 1 500GB drive (Drive D).
 

 I spent 2-days doing a new install of Win-7, reinstalling all my apps, and tuing the system so it was fast and reliable.  Then, prior to making a backup (bad), I downloaded the ISO image Ubuntu 12.04.1 LTS (64-bit) and then mounted it.  I then transferred the files to a 16GB USB flash drive.
 

 From the USB flash drive, I installed Ubuntu on Drive D the 500GB drive.  Ubuntu runs very well.  However, it surprised me that the installation created a dual boot option – I was expecting to change the boot order to select the operating system I wished to utilize.
 

 Once I shutdown the Ubuntu OS, I rebooted and selected the Win7 load option that was presented to me.  The system was extremely sluggish, a black screen intermittently appeared prior to a log-on screen finally appearing.  Once logging in the computer seemed to get into a look where it would show me the desktop and then present a black screen, which would stay on for a minute or more, then flash the desktop screen – this appears to be an infinite loop.
 

 Can I salvage my fast Win7 installation that I had achieved?  Is it possible to get the dual boot to work without crippling my Win7?  Failing that, is it possible to eliminate the dual boot and have the system work the way I envisioned by changing the order of the boot drives?
 

 I am in a time-sensitive project requiring Windows so a fix is desperately needed quickly.   
 

 Thank you for your consideration.

---

### Post by darkod on 2012-09-15
It doesn't make any sense. From the moment you select windows in the grub2 boot menu, the boot process is continued by the windows bootloader just as if you never have linux. Ubuntu has nothing to do with what is happening during the windows boot and windows functioning.

The installation creates dual boot menu by default when it detects two OSs. You can disable this if you want to, but first check if you still have windows bootloader on the other disk. Simply boot from the other disk and you shouldn't get the grub2 menu.

---

### Post by jcbaird on 2012-09-15
> **darkod said:**
> It doesn't make any sense. From the moment you select windows in the grub2 boot menu, the boot process is continued by the windows bootloader just as if you never have linux. Ubuntu has nothing to do with what is happening during the windows boot and windows functioning.

The installation creates dual boot menu by default when it detects two OSs. You can disable this if you want to, but first check if you still have windows bootloader on the other disk. Simply boot from the other disk and you shouldn't get the grub2 menu.
Thank you very much -- your comment gave me the confidence that the dual boot installation was not responsible -- I used window restore to go to a version before installing the ISO mount software and everything is now great -- thank you again very much for your consideration in providing a response to my question.
John

---

