---
title: "installing ubuntu on desktop with 2 x radeon 7850 crossfire cards"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by chaoschild.1st on 2014-01-05
Hi,

I've searched a bit on the net as well as this forum to try and find a solution to my problem with no luck - I've tried to install ubuntu 12.04.3 as well as 13.10 on my desktop, the specs are as follows:
[LIST]
[*]ASUS P8Z77-V PRO motherboard
[*]Intel i5 3570K CPU
[*]2 x Radeon 7850 graphics cards in crossfire mode.
[/LIST]

I've made a bootable USB stick and when booting up from the stick on the desktop, I get a text-based menu with "Try Ubuntu" or "Install Ubuntu", if I select either of the options, it just gets to a blank screen (backlight is still on) and the PC hangs.

I found a few threads with other users experiencing similar problems either during the installation or with an already installed Ubuntu when switching to crossfire mode with the graphics cards. Unfortunately none of the threads I found provided any sort of solution that I could try.

Is there a problem running Ubuntu with radeon crossfire'd graphics cards? And can it be resolved?

Thanks.

---

### Post by chaoschild.1st on 2014-01-07
*BUMP

Anybody? :)

I would very much prefer not to rip out one of the graphics cards from my machine to get Ubuntu going.

---

### Post by oldfred on 2014-01-07
I only have one older nVidia, so do not know about AMD.

Have you reviewed these links?

 The AMD Radeon Performance Is Incredible On Linux 3.12
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)

   [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

 [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by Bucky Ball on 2014-01-07
When you get that 'Try' 'Install' screen you could try hitting F6 and choosing 'nomodeset'. That might get you to a desktop so you can start experimenting with drivers. You could then start digging through oldfred's links.

---

### Post by Jake_Paine on 2014-03-03
If it's of any help at all, I've just installed Ubuntu 13.10 on my desktop running 2x 6870's in Crossfire setup with no issues. Everything worked perfectly out of the box. My motherboard is a Gigabyte 990FXA-UD3 with a AMD Athlon x4 CPU.

---

