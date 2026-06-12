---
title: "Dual boot question"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by bravo_elf on 2005-07-22
When I install Kubuntu, and choose the auto configuring option for HD tables, I get the "/" partition and "swap" space. 
    So my question is: where does it write the bootloader configuration? Or I must to define it manually and set a "boot" space to make a dual boot available?, like in Fedora Core where it was approx 100mb.

---

### Post by FLeiXiuS on 2005-07-22
The boot is simply a folder called /boot.  You can create a seperate partition for this folder.  Some find it useful as to where it'll have major security benefits / convenience.  I like doing it my self.  Creating roughly around 50 megs for this folder.  It helps to have things organized.  Format it as ext2/3 whichever.  As to thats the easiest to troubleshoot.  It's almost the most stable.  Thats just how I like doing it.  Users have their own opinions.

---

