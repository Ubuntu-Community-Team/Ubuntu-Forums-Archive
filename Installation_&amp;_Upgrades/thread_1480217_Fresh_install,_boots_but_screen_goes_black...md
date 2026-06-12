---
title: "Fresh install, boots but screen goes black.."
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by rebman on 2010-05-11
First post here,
 
Here are the specs of my current PC:
 
 
**CPU**: AMD Phenom II 955BE @ 3.5 
**Motherboard**: ASUS M4A89GTD PRO 
**Bios**: American Megatrends V. 1104 
**Graphics Card**: MSI Hawk Radeon HD 5770 
**Memory**: DDR3 4096Mb 
**Hard Drive**: SATA 500Gb 
**Optical Drive**: 21x DVDRW +/- 
**Power Supply**: ULTRA 750W PRO 
**Display**: DELL 22" 
**Case**: ROSEWILL SMART ONE 
**Sound Card**: Realtek ALC892 
**Mouse**: USB 
**Mouse pad**: Sand Paper 
**Keyboard**: USB 
**Operating System**: Windows 7 Ultimate x64 
 
 
 
So here's my problem, I downloaded and burned Ubuntu from ubuntu.com (64bit version) while in windows 7 64 i popped the install disc in, and it went into a setup in which it installed it asked to reboot, and I allowed. upon reboot boot I could choose either Windows or Ubuntu, so I picked ubuntu and off it went. It started to boot into the (Ubuntu) OS, it shows the little ubuntu thing, then the display goes black, like there is no signal to the monitor. The PC still runs, and reconizes when I plug in an iPhone or something, there is just a black screen though. I would like to know how to go about fixing this?
 
Thanks!

---

### Post by dino99 on 2010-05-11
seem to be an Ati issue, try to boot into recovery mode and add video=vesa on the boot line (edit it into grub menu, press "e", add video=vesa after "quiet" and remove "splah", then press ctrl+x to boot.

---

### Post by rebman on 2010-05-11
> **dino99 said:**
> seem to be an Ati issue, try to boot into recovery mode and add video=vesa on the boot line (edit it into grub menu, press "e", add video=vesa after "quiet" and remove "splah", then press ctrl+x to boot.
 
 
I can try that when I get home from work, thanks for your quick response. How do I go about getting into recovery mode?

---

### Post by dino99 on 2010-05-11
its the 2d line into grub menu, select that line, then edit it. If you dont see the grub menu, at the end of bios process, hold "shift" key down to see it.

Other way, if you can open a console (ctrl+alt+f2), then run:

sudo aticonfig --initial -f

[http://www.google.com/search?client=ubuntu&channel=fs&q=5770%2Blucid&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=5770%2Blucid&ie=utf-8&oe=utf-8)

---

