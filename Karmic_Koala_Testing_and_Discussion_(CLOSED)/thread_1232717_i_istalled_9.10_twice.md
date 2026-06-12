---
title: "i istalled 9.10 twice"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jimbean on 2009-08-05
i installed ubuntu 2 times by mistake is there a way to uninstall the 3 gig install with out messing with the 244 gig install 
ive already installed gparted

---

### Post by starcraft.man on 2009-08-05
Just select the partition holding the uneeded install and then delete and merge the free space whatever partition you want to add to. There's no such thing as uninstall with OSes, you just delete. See [gparted ]("http://gparted.sourceforge.net/documentation.php")docs if your uncertain how to do.

I hope ya didn't make one huge 244 GB root, root directory only needs at most 10 or 12 GB. Should make rest /home to save user files in case of reinstall.

Note: Also hope you realize 9.10 is still in development, if you want a stable version use 9.04.

---

### Post by Ji Ruo on 2009-08-05
> **jimbean said:**
> i installed ubuntu 2 times by mistake is there a way to uninstall the 3 gig install with out messing with the 244 gig install 
ive already installed gparted

Sure. If you have your live cd, just boot into it, enter gparted and select the 3 gig partition, then under edit choose delete. Then you can choose the 244 gig partition and select 'resize/move' to expand it over the empty space. If you did it right, click 'apply'.

The live CD is best, because you can't edit an active partition. So booting the 3 gig partition will mean that you can't delete it, and booting the 244 gig partition will mean that you can't resize it.

---

### Post by overdrank on 2009-08-05
Moved to Karmic Koala Testing and Discussion

---

### Post by jimbean on 2009-08-06
which partitions
/dev/sda3
/dev/sda2 this one and the next2 in order have a key next to them
dev/sda7
dev/sda8
dev/sda5
dev/sda6

i am using gparted the gui in ubuntu

---

### Post by ranch hand on 2009-08-07
You should never use gparted on the drive you are working on.  Boot your LiveCD and do it from there.

I am using 3 drives on my box so I can use gparted from the computer.  If I need to mess with sda I can boot to an OS on sdb and use gparted from there.

The only thing you can do is boot to the Live CD.

---

### Post by jimbean on 2009-08-07
thankyou i will try it

---

