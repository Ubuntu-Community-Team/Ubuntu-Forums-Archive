---
title: "Xp-Ubuntu Dual Boot PLZ HELP"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by invader7 on 2007-06-22
Hi.. I am new at ubuntu forums and i am very glad to be a member.... I have a problem with my ubuntu... I have 4 HDD... 3 of them are Sata and 1 is an 4GB IDE disk.... 

The Situation: I have ubuntu at 1 Sata HDD and Xp at 4 GB ide... I had ubuntu installed first and then i installed xp and reinstall grub... now the problem is that when the pc starts goes to grub menu and load ubuntu... i can't boot into xp.... i tried to play with menu.lst but nothing happend... my device map is this :

(fd0)	/dev/fd0
(hd0)	/dev/sda XP
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd Ubuntu

but at menu.lst in ubuntu i have to put 0,1 to load ubuntu.... i don't know what's going on.... i want to fix my dual boot... THANKS AND SORRY FOR MY BAD ENGLISH ;)

---

### Post by akshayas1986 on 2007-06-22
Hey buddy,

Well from my past experience, I can say that if you want to have all your OSes to appear on GRUB, you need to install them on the HDD's of the same type.. If your MBR is on Sata, you are expected to load XP and Ubuntu on Sata.. There is some problem with one OS being on IDE and the other one on Sata.

I just re-installed my OSes.. I know this is not the best solution so I hope someone else will come up with a better soution..

Akshaya Srivatsa

---

### Post by Ultra Magnus on 2007-06-22
Try typing in the terminal:

code: sudo fdisk -l

this should bring up all the available partitions - you should get something like
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        4523    36275200    7  HPFS/NTFS
/dev/sda3            4524        6447    15454530   83  Linux
/dev/sda4            6448       14593    65432745    5  Extended
/dev/sda5            6448       14411    63970798+  83  Linux
/dev/sda6           14412       14593     1461883+  82  Linux swap / Solaris

(ignore the dell utility bit - thats just mine!)

in the menu.lst file to boot ubuntu mine says (hd0,2) and windows is (hd0,1) 

windows should have an entry like this at the bottom of the file

title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

If you make changes to the menu.lst file, make sure to back it up - also you can edit it at the boot sequence

---

### Post by Vola on 2007-06-22
if Xp is on the first partition of the first disk put this in the menu.lst

title Windows XP
root (hd0,0)


hd0,0 is the first partition of the first disk (don't put SDX, grub works in it's way)

if xp is on the second partition or on a logical you need 

hd0,1  the logic is hdDISK,PARTITION   starting from zero

---

