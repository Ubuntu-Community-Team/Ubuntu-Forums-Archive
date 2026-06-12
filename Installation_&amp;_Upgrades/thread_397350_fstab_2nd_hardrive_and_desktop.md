---
title: "fstab 2nd hardrive and desktop"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by linuxfan128 on 2007-03-30
when i first installed ubuntu fiesty fawn i had to go to places then computer and click on a 28.8 gb volume enter password to make my 2nd hard drive appear on my desktop. it appeared as disk. it also apeared as disk in my places menu. now i edited my fstab to make it mount automaticly with no password but it doesnt appear on my desktop or places menu. it mounts because i can go to /media/storage to see it mounted. How do i make it show as a drive on my desktop and places?

here is my info
christopher@chrispc:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3736    30009388+  83  Linux

FTSAB
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f47e0cef-59e6-4d18-a86a-b2e5e5e0272c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1d16d3aa-724b-4e8a-8628-2d50552cc775 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/storage  ext3    defaults 0 0

---

### Post by orb9220 on 2007-03-30
Did you create a folder in /media called storage ?

---

### Post by linuxfan128 on 2007-03-30
> **orb9220 said:**
> Did you create a folder in /media called storage ?

Yes, I did that.

---

