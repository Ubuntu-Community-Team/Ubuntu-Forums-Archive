---
title: "Triple boot:  XP, 9.10, Debian"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by kat3c on 2010-03-05
I've got a dual boot of XP and Karmic, and want to add Debian.  I'm planning on freeing up 30GB or so of free space for the new install.  Currently I have (approximate numbers from my memory):

XP:  primary 66 GB
Ubuntu:  Right after the Windows partition is the extended partition of 54GB made of logical drives:
         1)  Root, 15GB
         2)  Swap, 2 GB (double my ram)
         3)  Home, the rest, about 37 GB

Booting using Grub.


I was planning on just using Gparted to shrink the Windows by 20GB to free up the new space for Debian.  I've downloaded and burned an image of the Debian install disk.

Should I pre-partition the free space into root/swap/home, or just root/home and can I then use the already existing swap?  Or, will the Debian disk take care of partitioning if I just tell it to install on the unallocated space?

Thanks for any help.

---

### Post by Barriehie on 2010-03-05
I would do all the partitioning before installing Debian.  I say this because I had my ubuntu install using a $HOME on another partition and for some reason Debian didn't find it.  You should be able to use the same swap partition for both OS's.  I know you can't use the same $HOME partition, have to have diff. usernames for the ubuntu install and the debian install.

HTH,
Barrie

---

