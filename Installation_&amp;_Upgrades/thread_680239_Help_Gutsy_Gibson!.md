---
title: "Help Gutsy Gibson!"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by 5starog on 2008-01-27
][SIZE="7"]Yeah so i have two hard drives one windows and the other blank. I formatted the blank one deleted all partitions, and I'm trying to install Ubuntu on the blank one. So i downloaded the iso and burnt it on three different cds just incase. When i try to install it i get through everything except when the main install thing comes and gets stuck on 15% Detecting file system. EVERYTHING iS FROZEN usb keyboard ps2 keyboard usb mouse and ps2 mouse are all stuck nothing move the num lock doesn't work, its just frozen I tried this 17 times it always gets stuck and yesterday i even ;left it for five exact hours

I tried it in safe graphics mode, scanned the cds for errors and checked the memory (no errors) and still its stuck on 15% I read every single post here about that problem so pls dont post those links again. SHOULD i just try the alternate installer?

I have Intel Celeron 1.80 ghz 256 DDR1 ram (old I kno) MAxtor 31536H2 (ubuntu) look here [http://www.hd4less.com/maxdiammaxvl7.html](http://www.hd4less.com/maxdiammaxvl7.html) and a Smasunf 40 gb (windows) and video car is SVG PRO SAVAGER 32 mb

AnotheR question, after i install Ubuntu can i make the windows master and ubuntu slave and use the windows MBR instead of GRUB. And I know that I can install GRub on a floppy to keep my windows mbr [http://ubuntuforums.org/showthread.p...ng+windows+mbr](http://ubuntuforums.org/showthread.p...ng+windows+mbr)
Should I do that or should i just make ubuntu master and windows slave and configure the grub menu after. I'm going to use windows 95% of the time

---

### Post by chewearn on 2008-01-28
First question:
Yes, you should probably just try the alternate installer disc.

Second question:
No, Windows MBR is not Ubuntu/Linux aware, so you will never be able to use it to select OSes.

But, yes, you can keep Windows in primary and still retains it MBR.  You put ubuntu in slave, and during installation (this is important!) tell the ubuntu installer to put grub into the slave harddisk, so that the Windows MBR is not overwrite.  Then, change your boot disk in BIOS to the slave harddisk; that way, grub will start.  Further, you edit menu.lst to change the default boot OS to Windows.

---

