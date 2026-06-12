---
title: "Unable to Install Due to White Lines"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by trentkillinger on 2013-10-30
Hello, If anyone could help me I would be gratefull. Ive sucsessfully installed Ubuntu 13.04 on my laptop. I have come acustomed to ubuntu and wish to install it on my desktop. When trying to install it on my desktop I seclect install to hard drive but after the ubuntu loading screen I get white lines. I can see the cursor on my screena and here a sound when the white line pop up. I have included and image so you canen see the problem i have. I also have tried to use only one monitor but it does the same thing. If anyoone could help me i would be greatfull.

Thank you

System Specs:
3570k
Asus Maximus v 
AMD 7950 Crossfire
8gb ram
Installing from a SD card

---

### Post by coldraven on 2013-10-30
I'm guessing that you have to edit the grub boot menu and add "nomodeset". I just Googled "Ubuntu nomodeset" and one of the top results was this:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I think that you get to the grub menu by holding down the shift key during boot-up.
It seems that once you get to a working desktop you should be able to configure your video card properly.

---

