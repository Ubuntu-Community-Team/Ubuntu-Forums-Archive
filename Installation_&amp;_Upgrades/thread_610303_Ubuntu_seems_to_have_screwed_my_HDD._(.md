---
title: "Ubuntu seems to have screwed my HDD. :("
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Brandnew70x7 on 2007-11-11
I wen to install the AMD64 version of 7.10 and it was a total failure. Got HAL errors, wifi didn't work. Etc. Alright whatever, I figured I'd restart. 

I restarted and tried to go into vista... and it restarted on its own. Tried this twice more and more restarts.

Moving on, I figure I'll put my HDD in a USB housing, hook it up to my mac and reformat it. Okay thats done. I try installing XP, 2000, 98, and Vista and they all restart. I can't even get to the actually installation process...

ANYONE have experience with this? I had no problems until I tried to install Ubuntu. Any help is greatly appreciated.

ASUS M2N-SLI
AMD Athlon X2 6000+
GeForce 8800 GTS
4 GB of DDR2 RAM
500 GB Western Digital SATA drive

---

### Post by 2shanfernando on 2007-11-11
> **Brandnew70x7 said:**
> 
Moving on, I figure I'll put my HDD in a USB housing, hook it up to my mac and reformat it. Okay thats done. I try installing XP, 2000, 98, and Vista and they all restart. I can't even get to the actually installation process...


Strange, I'd try a MemTest and see if it atleast does 1-pass. When the windows installer restarts, does it bluescreen and restart (if so what do you get?). More importantly where does it restart?

I would also reformat the 500Gb drive properly, if you can boot the LiveCD use GParted and delete the partition and try redoing the windows install.

---

### Post by Brandnew70x7 on 2007-11-11
Thanks for the reply.

I'm currently doing a one pass erase of my drive using Active KILLDISK from the Ultimate Boot CD.

I just bought this HD and I really dont want to pick up a replacement :(

I tried using every stick of memory on its own and got no results. And boy was it tedious.

---

### Post by froy02 on 2007-11-11
Boot with the CD utility software that came with your hard drive and repair the mbr or just format it using the western digital  utility. If you don't have the disk you have to download it and make a bootable cd. 
Also the XP installation disk has a utility to fix the mbr (master boot record).

This is assuming that it is configured properly in the bios as the master drive and also as the boot drive.

---

### Post by Brandnew70x7 on 2007-11-12
This is driving me nuts guys..

Just did a total one pass reformat took about an hour + (Ugh)

and still no dice. I really think Ubuntu broke my HDD, as ridiculous as that sounds.

XP restarts the computer abruptly at "Setup is starting windows" or whatever

Vista restarts abruptly without warning also, at the loading screen with the moving green bars.

---

### Post by bulldog on 2007-11-12
I don't think it's the hdd,something else is malfunctioning.
If you have a live cd it should just boot,if that's not happening,well,check the whole pc.

---

### Post by Brandnew70x7 on 2007-11-13
Just tried a new DVD drive. Nothing.

I tried each stick of memory individually, nothing.

The only thing Ihaven't tried is a new HD because it's not here yet.

---

