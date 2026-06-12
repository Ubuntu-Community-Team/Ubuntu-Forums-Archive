---
title: "Feisty and External USB Drive Grub Issue"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by gjm777 on 2007-05-06
Well, after a few days of messing around with this I am going to post here.
I can install Feisty just fine from a live cd to my external 120gb HD. I make sure that GRUB is installed to the external drives MBR (hd0) 
Once I reboot though, I get dumped right to a grub cmd line. No menu or anything.
geometry ( finds only (fd0) and nothing else. I cannot find anything related to my grub files either.
"find /boot/grub/stage1" nothing is found.
It's almost like grub cant see the partitions on my usb drive at all. Any help would be much appreciated!

my regular partition scheme is the following:

10g /
2g swap
20g /home

---

