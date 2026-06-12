---
title: "moving ubuntu from one partition to another"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by francois.e on 2010-12-09
I work with ubuntu 10.10 64 bit on a hp pavilion 2713ca laptop. Everything is fine presently, except for the fact that I will be soon out of space on the actual sda6 partition (only 2 gig left). 

I would like to move the ubuntu partition with all its content to a second one where there is a lot of space, that is sda2. So my question would be twofold. 

1) What software can I use to do that (gparted, clonezilla, ... ) and is someone is familiar with the procedure?

2) Will there be an easy way to change the grub.cfg file? (for example, will the command grub update be enough to boot to new setup)

Is is that easy?

---

### Post by oldfred on 2010-12-10
I assume sda6 is not near sda2, so you can not easily move partitions around to make more space in sda6. Or how large is sda6. You could make sda2 as /home which will have all your data. A / (root) only needs to be 10-20GB if all you data is in another partition.

Gparted will work. You will have to reinstall grub and edit fstab with new UUIDs or sdaX numbers.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

---

