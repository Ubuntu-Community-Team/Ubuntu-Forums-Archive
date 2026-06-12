---
title: "First Time Linux User; Linux w/ Windows 7, no bootloader options"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by TheKbob on 2010-03-09
Hey guys, first time user of Linux.

I have a machine that has a partitioned single harddisk that I first installed Linux 9.10 on and then the second partition has had Windows XP installed and then a Windows 7 upgrade performed on it.  Both are 64 bit.

I have been doing lots of research on re-acquiring "GRUB" as it seems to have boot options between Ubuntu and Windows 7.

I have a live disc and I boot into that.

I open the terminal and I try to follow this guide:

[GRUB install guide from this forum]("http://ubuntuforums.org/showthread.php?t=1035999") 

This is where I hit issues.  I cannot find the "stage 1" files.

Firstly, it says that I do not have GRUB at all and I must install it, which asks for a downloader and ownloads the selected files and puts them who knows where.  I can find the files of "Stage1" and what not under USR folders on the bootable CD (at least I think I am), but I cannot copy and paste these into the BOOT folder of the actual harddisk.

I am probably not explaining the problem well enough as I am new to Ubuntu/Linux.  The only command line I have used before it MATLAB, so I'm not very good with Linux commands. 

Any help or ideas?

Edit: Problem Solved.

---

### Post by darkod on 2010-03-09
Ubuntu 9.10 comes with grub2 and not the older grub1 (or grub legacy). Those instructions are for grub1. Read the instructions here and focus on the instructions for 9.10:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by TheKbob on 2010-03-09
Thanks, I'll give this a whirl and see where it gets me. Stay tuned!

---

### Post by TheKbob on 2010-03-09
Alright, I'm back to Linux... but now I didn't get an option to pick an operating system! 

Any tips on this that would save me an hour like your last one?

---

### Post by wilee-nilee on 2010-03-09
Run sudo update-grub in the terminal and see if it includes all the OS for grub.

---

### Post by TheKbob on 2010-03-09
Hey, thanks!

Great forums here. I'm a research assistant and was charged to setup a lab computer for MATLAB on both Linux and Windows.  I built this machine and it's my first dual boot and usage of Linux.  Love the resources here.

I'm going to attempt to boot a 6 year old laptop with Linux to do some work at home.  How good is Linux as recognizing old graphics chips in laptops?

---

### Post by wilee-nilee on 2010-03-10
I would use a live cd to check if the graphics card is supported chances are that it will be, but be sure with a little test run live.

---

