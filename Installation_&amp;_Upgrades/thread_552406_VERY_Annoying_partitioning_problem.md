---
title: "VERY Annoying partitioning problem"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by neonl on 2007-09-16
hi, I'm trying to install ubuntu 7.04 from the live CD. Everything it's fine until I get to the partitioning part. I want to create a partition table like:

/sda1 - / (10GB)
/sda2 - swap (2GB)
/sda3 - /home (290GB)

My sata HDD has 320GB (I want to leave a few GB unpartitioned for Windows XP),

The problem is that when I try to create the big partition he says: "You can't the end before the beginning". I tried to do extended and logical partitions and primary partitions, The interesting part is that when I install my HDD with the Alternate CD this doesn't happens...

Help????

---

### Post by Pumalite on 2007-09-16
If you are planing to install XP; you better install it first, then Ubuntu. If you want to  partition your hard drive, there is Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone, burn to CD, boot from it, program)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

