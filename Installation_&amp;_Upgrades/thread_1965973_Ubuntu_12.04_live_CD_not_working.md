---
title: "Ubuntu 12.04 live CD not working"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by padre0 on 2012-04-26
Hi, I want to make a clean install of Ubuntu 12.04 LTS. I've downloaded the ISO file from [www.ubuntu.com](www.ubuntu.com).

When I'm inserting the CD, it start booting, but it stops just before the screen where I have to choose to install or try Ubuntu. The purple screen is displayed, then I get the screen from the picture and the system is blocked. The configuration of my desktop is: AMD Athlon II x3 440 3.0 GHz, 4G DDR3,NVIDIA GFORCE GT 240

I tried to boot the CD from my laptop and it worked just fine.

I also tried 10.10, 11.04, 11.10 and they are not working; I tried them a long time ago (when they where launched) and I can't remember the exact behaviour.

[IMG]http://imageshack.us/photo/my-images/13/20120426220848.jpg[/IMG]
[IMG]http://imageshack.us/photo/my-images/88/20120426220842.jpg[/IMG]
The picture show a balck screen with some red, green or blue small dots.

---

### Post by DougC on 2012-04-26
I had a similar problem.

At the boot screen (the one with the man and the keyboard) press any key.

You will then have menu's at the bottom. Press F6 and then select nomodeset

press enter and you should boot.

For me it only booted into a lowres 2D unity screen. But I could install.

I found install very slow. I think everyone was hitting the update servers and for smoe reason the nVidia drivers had not installed. So i rebooted ( had to add nomodset to the kernel line) and installed the nVidia drivers from the icon at the top of the screen. I'm all fine now proper resolution and I don't need the nomodset option anymore.

---

### Post by padre0 on 2012-04-26
Thank's, it worked to install, but Ubuntu is not loading. I'll try to fix it somehow, and if it won't work, I'll ask for help again.

---

### Post by DougC on 2012-04-26
Check this old thread:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You need the section: "How to temporarily set kernel boot options on an installed OS (not wubi)"

Once you can boot get the nVidia drivers installed. You should be ok after that.

---

### Post by jadtech on 2012-04-26
yup 2d will work the issue is  video driver  there is a bug  with the nivida driver  can get the same issue with AMD ATI as well ..

---

### Post by DougC on 2012-04-26
The nVidia driver worked fine once I got it. The problem was just getting it to  boot so I could get it.

Still all fine for me now.

---

### Post by padre0 on 2012-04-27
Thank you, I will try to fix it and I will let you know how it worked. But for now I have no time, so it will be only next week. 
Have a nice weekend!

---

