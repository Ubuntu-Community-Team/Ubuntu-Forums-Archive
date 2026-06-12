---
title: "Fails at 'Copy remaining packages'"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by jgb2185 on 2005-07-31
I have partitioned the slave disk (120 MB Maxtor) in my Dell Optiplex GX110 as follows:

/dev/hdb1      ext3    20 MB    boot
/dev/hdb2      swap   512 mb    swap
/dev/hdb3  extended
[INDENT]/dev/hdb5      ext3    12 GB   root
/dev/hdb6      ext3    20 GB   home
/dev/hdb7      ext3    12 GB   unused
/dev/hdb8      ext3    12 GB   unused
/dev/hdb9      ext3    20 GB   unused
/dev/hdb10     ext3    30 GB   unused
[/INDENT]
I used the built-in partitioner to format the partitions and set the mount points. The Ubuntu 5.04 installer fails at 'Copy remaining packages to hard disk'. Trying a variant of the partitioning scheme where /dev/hdb7 is mapped to /usr and /dev/hdb8 to /var results in the same failure.

Can anyone suggest what it is I am doing wrong, please?

---

### Post by adwait on 2005-07-31
I would check the MD5 sum of the ISO before burning. Also, try burning another CD, in the dis at once mode, and at a lower speed......say 24X

---

### Post by Copter on 2005-08-01
i had the same problem while ago. i have 40gb usb hdd and dvd-ram drive.

my solution was :: abort instalation, reboot, install again & repartition. it worked fine for me :)  dont know what that was. ive been istalling kubuntu four times and it happend only once.

copter :]

---

### Post by jgb2185 on 2005-08-02
Burning at a slower speed seems to have done the trick. Thanks to all who replied.

Now I have a [GRUB error](http://ubuntuforums.org/showthread.php?p=283929) to deal with...

JGB

---

