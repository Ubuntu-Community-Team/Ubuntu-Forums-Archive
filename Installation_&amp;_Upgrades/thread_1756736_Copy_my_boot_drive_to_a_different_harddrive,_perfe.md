---
title: "Copy my boot drive to a different harddrive, perfectly"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by AndroidOcean on 2011-05-12
So here is the dilemma.

I am converting over to linux ubuntu 11.04, and I have used it for a week, love it.

I installed an old 30gb HDD in order to install it ubuntu to try it out.

Now I want to erase my primary windows XP drive and reformat to ext4, just like linux.


Is there any prog or method that will make a perfect copy of what I have on my current drive ubuntu and put it on the newly formatted drive primary, so that it can boot ubuntu will all of the stuff I have on it right now?

I dont want to go through recustomizing and downloading every single linux program again.

---

### Post by 67GTA on 2011-05-12
Gparted should handle this. It is a Linux based partition tool. Use a Ubuntu live CD. Gparted is on the live CD by default. Here is a how to [http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)

You may have to reinstall grub2 bootloader depending on your HDD setup. [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

