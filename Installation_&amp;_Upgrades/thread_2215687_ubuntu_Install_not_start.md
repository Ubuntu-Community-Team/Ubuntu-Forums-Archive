---
title: "ubuntu Install not start"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by darky2 on 2014-04-07
hello all :) 

i have a problem with ubuntu install 

[COLOR=#000000][FONT=Arial]I can boot on the live cd   is ok  :) 

[/FONT][/COLOR]the installation window does not open i have only a top menu


image 
[http://img15.hostingpics.net/pics/14188720140407195309.jpg](http://img15.hostingpics.net/pics/14188720140407195309.jpg)
pleez help

---

### Post by darky2 on 2014-04-08
up

---

### Post by su:bhatta on 2014-04-09
Did you checksum the downloaded ISO for faults?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by darky2 on 2014-04-09
is ok for my dvd or usb works on another computer 

my config 
asus p6tse
8 GB of ram 
Core i7 first generation
radeon 5700 hd

---

### Post by oldfred on 2014-04-09
I think Radeon's also use nomodeset.

I have nVidia and always have to use nomodeset to boot until I install nVidia's drivers.
But once I did get to a screen like that and was able to right click and if offered to change screen and from that I was able to get to system and click on software to install correct proprietary driver.

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

