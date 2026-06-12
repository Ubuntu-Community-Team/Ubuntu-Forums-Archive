---
title: "Ubuntu 13.10, dual boot Windows 8"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by EternallyAries on 2014-04-01
So before I continue, hello I am EternallyAries. I am quite new to Ubuntu, but I do have it on my old Windows 7 laptop as a dual boot.

Anyway, I will try and provide as much information needed to get this figured out. So I have a HP Pavilion Laptop, it has 8GB of ram and it runs on a Radeon Graphic Card along with a Quad Core. Not sure if you need more computer specs, but I'll sure get more if needed.

Anyway, I run Windows 8 not Windows 8.1 due to hardware problems. And after using Windows 8, I decided it be a good time to get Ubuntu on this laptop as a Dual boot. I've disable fast boot, and secure boot in the UEFI. Anyway, I burned Ubuntu Version 13.10 on a DVD RW. And place the disc inside the tray, and restarted my laptop. it gave me a black ubuntu screen instead of a purple like screen like this same exact one I pulled off the web.

[IMG]http://2.bp.blogspot.com/-lbCXvuI3flU/UclTr4kFwOI/AAAAAAAAARA/1x7Z6vp0RZc/s400/Screenshot+from+2013-06-25+16:23:08.png[/IMG]

It gave me no option to start Windows 8. But I ignored that and tried installing Ubuntu. It gave me a loading screen like this one.

[IMG]http://linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png[/IMG]

Sorry about the image size. But yes it started loading, and after that it went into a black screen, with no warnings, no install screen at all. It made me confuse as to why it did this. So I restarted my laptop by power button due to it being frozen. And tried booting the install again. It did the same thing. So this time instead of doing the install I tried the "Try Ubuntu without Installing" And it gave me the loading screen again, and it froze into a black screen again. I am not sure what is causing the problem, I tried researching it all over the internet. Nobody seems to have this issue. I hope someone here knows how to fix this so I can install Ubuntu on my laptop. It be wonderful.

---

### Post by oldfred on 2014-04-01
If you got grub menu from install DVD, then that was UEFI not BIOS/CSM. If Windows is UEFI then that was what you wanted.

Often after an install, video issues are a problem. I do not know AMD/Radeon as I have nVidia. But often need nomodeset or other boot parameters before installing proprietary driver. Verson of card can make a difference as current proprietary driver only supports newer cards/chips.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
 The AMD Radeon Performance Is Incredible On Linux 3.12
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)

   [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by EternallyAries on 2014-04-01
Thank you very much oldfred. I was able to boot it up entirely and install it. But now I have run into another problem. It seems to ignore Ubuntu entirely. And boots straight to Windows 8 with out asking which OS to boot too. Does anyone know how to fix this one issue?

---

### Post by oldfred on 2014-04-01
If UEFI, it does not automatically change UEFI default to boot grub/Ubuntu. You should be able to go into UEFI or use one time boot key to test if it will boot from Ubuntu entry.

A few vendors have modified UEFI to only boot Windows. Do not remember if HP was one or not.

---

