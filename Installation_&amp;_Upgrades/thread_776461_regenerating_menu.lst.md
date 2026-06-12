---
title: "regenerating menu.lst?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by anyduck on 2008-04-30
Before I upgraded from 7.10 to 8.04 my system was rock solid, I never had any problems. After the upgrade things took a nose dive. I get weird errors when booting, the screen resolution is off, my video drivers aren't working  and most programs have been behaving erratically. Even thou I'm fairly new at this, I'm 95% sure I know what went wrong and I only have myself to blame.  During the upgrade I was asked if I wanted to keep my menu.lst file. I now have since realized that it was a ***huge mistake*** to say yes. Thats it for the sob story. Now for the heart of the question at hand: 

How to I get the system to generate a new menu.lst file for 8.04?

---

### Post by El King on 2008-04-30
menu.lst is for the GRUB loader, i doubt that it has any effect on ur system performance
anyway u can use ur live cd and this thread to recover grub and regenerate menu.lst
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by eks on 2008-04-30
El King is right, it probably has nothing to do with menu.lst, which defines the menu for GRUB, the boot loader. On that file there's only information about where to finde the OS' on your computer (that is, where your Linux install is and/or your Windows install).

If you have your /home on a different partition (which is strongly suggested), you could try installing Ubuntu again from scratch on your / (File System) partition. If not, you could reinstall it anyways, but you will probably loose all your config files. 

It's not a bad thing anyway, I installed Ubuntu some 3 times until this one I'm on now because I tweaked everything so much it was easier to fix by reinstalling. I will probably do the same with Hardy now (but only when Firefox 3 is released), but mostly just because I want the default theme for a while.


Good luck! :)
eks

---

### Post by kellemes on 2008-05-01
> **anyduck said:**
> Before I upgraded from 7.10 to 8.04 my system was rock solid, I never had any problems. After the upgrade things took a nose dive. I get weird errors when booting, the screen resolution is off, my video drivers aren't working  and most programs have been behaving erratically. Even thou I'm fairly new at this, I'm 95% sure I know what went wrong and I only have myself to blame.  During the upgrade I was asked if I wanted to keep my menu.lst file. I now have since realized that it was a ***huge mistake*** to say yes. Thats it for the sob story. Now for the heart of the question at hand: 

How to I get the system to generate a new menu.lst file for 8.04?

menu.lst has nothing to do with the problems you mention.
You are installing a new os, so issues are to be expected..
Gettin your videocard going will make a big change for sure..

---

### Post by mwshook on 2008-05-02
I'm having the exact same problem...
I know why it happened. GRUB is loading the old version of the linux kernel. The video drivers need the newer kernel.
Now I just need to figure out how to fix it. :)

---

### Post by bobnutfield on 2008-05-02
This is not an unusual problem.  What is probably happening (and why Hardy is acting so odd) is because if you still have your original meny first, you are probably booting Hardy with the old Gutsy kernel.  Post your menu.lst and we'll see if that is the problem.

Bob

---

### Post by jpdamigaman on 2008-05-02
e

---

