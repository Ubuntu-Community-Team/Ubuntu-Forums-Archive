---
title: "cpu frequency scaling error"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Sephlaire on 2007-11-08
i try to run the live CD and get this error

[PHP]
/etc/rc2.d/S2Opowernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
*CPU freqency scaling not supported
[/PHP]

ive read other posts and tried typing 
[PHP]sudo dpkg-reconfigure gnome-applets[/PHP]

but that really didnt do anything and im not that experienced with installing ubuntu
here is my PC build that I have


XFX GeForce 7900GS 256MB 256-bit GDDR3 PCI Express x16
AMD Athlon 64 X2 5200+ Windsor 2.6GHz Socket AM2 65W Processor
ABIT AN-M2 nView AM2 NVIDIA Geforce 7025/NF630a Micro ATX AMD Motherboard
Kingston 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)

Any help would be appreciated... If you suggest i use the text-based installer, can you possibly link or direct me in the right way to something that will walk me through the text based installer.

---

### Post by beansdad on 2007-11-08
I have a similar message (briefly) when I have to power off my desktop after non-start after grub and have tried to get a solution to my non-start problems but with no success.

I can use the ISO CD to load and run Gutsy but not the Upgrade on the desktop.

Am thinking I'm going to have to do a full re-install.

Good luck - I've put two threads on about my prob but not much response so far!

---

### Post by beansdad on 2007-11-09
I've eventually installed from ISO CD and this seems to have cured my problem. You may need to do likewise.:(

---

