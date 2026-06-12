---
title: "Ubuntu installation"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by Skopuningurin on 2010-11-08
Hi

I got a little problem. I have Ubuntu 10.10 installed on my Laptop. But I want to get Ubuntu 10.04 on it. The problem is that I have 2 harddrives on my laptop ( 500gb each ) I have ubuntu 10.10 on one harddrive and Vista on the other.
How do I delete both partisons and only install Ubuntu 10.04?

---

### Post by dino99 on 2010-11-08
you have enough room to install a triple boot if you want to compare before erasing a partition. Prepare a partition to install 10.04 with gparted from 10.10:

- / ext3 or ext4 format, bootable, about 12 Gb
( take note of its name (/dev/sd?, to install on it when the "alternate" iso used in manual installation will ask on which partition you want to install it)

you dont need to create other partitions: swap is already created and can be used by all linux distro, /home is created too

as you already have grub-pc installed with 10.10, you dont need to install it again (need it only if you erase the 10.10 partition later)

---

### Post by thegod_slayer on 2010-11-08
> **Skopuningurin said:**
> 
How do I delete both partisons and only install Ubuntu 10.04?


well, if you installed ubuntu 10.10 with a dual boot, single os install shouldn't be a problem.
the whole whole process is similar to any ubuntu install just remember to delete the swap,/,and /boot (if you have made this partition) and also the windows partition at the partition table.
that's it then make your own partitions as you want and install 10.04.

---

### Post by Skopuningurin on 2010-11-08
Are you saying that I can install Ubuntu 10.04 with gparted. Boot into 10.04 and just delete the Ubuntu 10.10 and Vista without any problem?

---

### Post by thegod_slayer on 2010-11-08
sorry no experience with this kind of install.

insert the live cd, go to the partitioning table which will show both 10.10 and vista.
remove all that and make a single clean install.

see it's easy.

---

### Post by Skopuningurin on 2010-11-09
Is it possible to just delete the Windows partisions from Ubuntu ( In dicstools ), or formate the windows harddrive then put the CD in and just install it alone. ( delteing Ubuntu 10.10 while installing 10.04 ) ?
I am a complete noob.

---

### Post by dino99 on 2010-11-09
why not following #2 ?

use gparted or partedmagic to prepare your hdd, then install ubuntu and later (few days or weeks) if you think that you can remove a distro, you then use gparted to format the unwanted partition , but take care that grub is installed somewhere else if you want to be able to boot.

---

### Post by nm_geo on 2010-11-09
I just installed 10.4 on a XP box using Gparted from a live USB and it went so smooth I was shocked. You could shrink you windows partition on drive one and then install 10.4 from a CD or a live USB. Oh to have (2) 500GB drives. My Dell D620 laptop had a new 320GB drive and that ought to be plenty for a long time.

---

