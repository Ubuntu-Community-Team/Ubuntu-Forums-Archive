---
title: "could not mount hard drive"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-04-08
I am having 3 drives in my Windows OS..but,when i switch to ubuntu i can only see 2 drives..the missing drive has ubuntu installed in it..how to view all the drives of windows in ubuntu

---

### Post by ~Plue on 2011-04-08
did you install using wubi? if thats the case, the partition you installed ubuntu on would be in places > computer > file system > host

hope that helps

---

### Post by sandy0594 on 2011-04-08
It is the same as u said..Is there anyway in ubuntu to sort the drives as in windows..I mean in windows we have drives like **C**,**D**,**E..**So,can we expect something like that in ubuntu

---

### Post by Dutch70 on 2011-04-08
Sort of...but they are called partitions. 
sda1, sda2, sda3 and so on.

Different physical hard drives would be...
sdb, sdc, sdd, etc.

Maybe some pictures will help you understand the naming process. This is 2 different physical hard drives, sda & sdb. Inside them you'll find sda1, sda2, and the other would be sdb1, sdb2.

---

### Post by ~Plue on 2011-04-08
its one of the big difference between *nix and windows.. the file system
all unix style systems have a single hierarchical directory system with the root directory of **/**. partitions are files with **/**dev/s(h)dXx labels and can be mounted any where in the fie system (/media/123, /mnt/321) 

but in windows  there are multiple 'root' directories, each with a letter corresponding to a specific drive. like c:\ d:\

so the closest to a windows like naming scheme is to give the partition a letter as the label you want using gparted or the gnome disk utility in system > administration, then it'll appear so from the places menu or places > computer, and will be mounted as /media/C and on...

//btw, if to install ubuntu the 'normal' way, all partitions would be accessible directly from the places menu, or if you prefer the current installation, you could add /host to you bookmarks in nautilus (press ctrl+d from the directory)

---

### Post by sandy0594 on 2011-04-08
Thank you guys,i understood the format..Thanks for ur time

---

