---
title: "Network Install from USB drive - Only boots with USB pluged in."
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by james_2002uk on 2007-06-02
Hi. I'm pretty new to Linux, to cut a long story short my XP installation went into meltdown and left my system unusable and to make matters worse my CD drive is broken! So I did a network install from my USB drive (Quite scary for a first Linux install!). 

Everything installed perfectly which is great. The only problem is that the system only boots up if the USB drive is plugged in. Is there a way to fix this so it will boot from the hard disk?

Thanks allot!

Jim

---

### Post by james_2002uk on 2007-06-03
For anyone else who has this problem i managed to sort it out pretty straight forwardly. Just type
#sudo fdisk -l 
to find which disks are bootable and then amend the menu.lst file to the right disk (in my case from (hd1,0) to (hd0,0))!

---

