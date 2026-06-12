---
title: "Help with partitioning of SSD 64MB?"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by xcislav on 2011-06-04
I'm planning to use this system for virtual machines (16GB RAM)
Have I to make a ramfs from fdisk or just edit /etc/fstab afterwards?
none /var/tmp/portage tmpfs noauto,nr_inodes=1M,size=2500M 0 0
none /tmp tmpfs defaults,noatime,mode 1777 0 0
Advise me yourselves how you'd consider planning SSD 64MB by partition size providing that I want to maximize usage of ramdisks. To make one real partitions or a few of them?
See:
/
/boot
which partitions to make and how much space per partition 
/home
/var
/tmp
/usr
/opt
/etc
Perhaps FS would be reiserfs for /tmp and /usr/tmp/portage
Would it be better making swap (apart) or beforehand or don't make swap at all... Or how to just make swap to ramfs?

These are main keypoints, and are very important

---

### Post by oldfred on 2011-06-04
Have not used virtual machines, so that may change it somewhat.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

