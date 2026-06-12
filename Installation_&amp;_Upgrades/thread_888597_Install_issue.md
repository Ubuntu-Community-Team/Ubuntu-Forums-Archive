---
title: "Install issue"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Chondro_Biak on 2008-08-13
I am banging my head against the wall here... 

I have built a new computer:
GIGABYTE GA-EP45-DS4P LGA 775 Intel P45 ATX Intel Motherboard
XFX PVT96GYDDU GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16
SAMSUNG SH-S223F DVD Burner
Intel Core 2 Duo E8500 Wolfdale 3.16GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
Kingston HyperX 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 KHX8500D2K2/2G

and I am trying to load Hardy on it. I get thrugh the install perfect... But then I reboot and get the splash screen, that shows the load bar it stops at like 1/16". If I hit crtl+alt+F1 it shows the video card resolution failing... It fails 4 times and bring me to some funky kind of terminal... 

So I have identified that the drivers for my video card are not there yet. I have identified that I can fix this problem by installing ENVY (just one option)... 

So my question is, how do I fix this? I can not get to a normal terminal to install Envy and I can not get to a terminal to edit my x server. 

Any suggestions?

---

### Post by Kevbert on 2008-08-13
Did you check the ISO file that you downloaded with [[COLOR="Red"]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") (checksum) ?
Did you burn the CD at the slowest speed possible and then perform a CD check ?
Have you performed a memory check (via the CD memory ?  It's possible to run Windows with dodgy memory.

---

### Post by Chondro_Biak on 2008-08-13
I did burn the DVD at 4x speed and I did do a cd check before I installed using the cd's cd checker. 
I did not check it with md5sum, however I have downloaded and burned copies for 7.10 standard and alt as well as the 8.04 standard and alt and get the same thing. 
Also I have used the same DVD to install Hardy on at least 5 other computers. I did burn a new copy just in case the DVD was dammaged and I did not see it, using the same iso used before and I get the same issue on the boot.

I am pretty sure this is a video card issue?

---

### Post by Kevbert on 2008-08-13
Looks like you've done everything correctly.  You say you can get to a 'funny kind of terminal'.  Does that come up with a $ or # sign ?  If so you can use nano to edit your xorg.conf file with
```
sudo nano -w /etc/X11/xorg.conf
```
What you need to edit and change at this stage I'm not sure of ?  Maybe there's someone else who can help....

---

### Post by Chondro_Biak on 2008-08-13
The terminal is not accepting what I consider normal terminal commands. sudo is not a recognized command. I think the terminal is called busy box of something like that...

---

### Post by jimmyhacker on 2008-08-13
i get same error.md5sum gone good,but installation fails and monitor is screwed:lolflag::lolflag:fuccin OS

---

### Post by Chondro_Biak on 2008-08-13
Jimmy
Is yours popping up with busy box?

---

