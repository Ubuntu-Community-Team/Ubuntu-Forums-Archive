---
title: "Installing other  linux OS"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by chezerian on 2010-08-09
I am currently using ubuntu 9.10 and would like to use other OSes such as Debian and Arch and so on and would like advice on how to partition my hard drive.

My hard drive is partitioned as follows 175 Gb (for OSes), 9 Gb used  (/dev/sda1 mounted as root and a boot flag)

750 Gb used as home and the rest og the 931 Gb hard drive as linux-swap.

Or look at the picture.

My question is how should i go about partitioning the hard drive. My guess would be to create a new partition to the left of sda1 and the n install an OS on that. Would that lead to problems or is there a better way ?

---

### Post by oldfred on 2010-08-09
Just shrink sda1 to 20GB or so as that should be plenty. Then you can create additional 20-25GB root partitions for additional installs.

You should not share /home as that can cause issues with different systems using different versions of software. But you can share data. Shrink you current /home and create a /data partition for data. My home is now only 1GB as all my data is in the /data partition. I even move some hidden folders like firefox & thunderbird into shared data so I have all the same info in all installs.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

