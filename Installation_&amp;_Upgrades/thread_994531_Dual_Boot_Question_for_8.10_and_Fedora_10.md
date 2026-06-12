---
title: "Dual Boot Question for 8.10 and Fedora 10"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by MerlinsLair on 2008-11-26
Hi,

I'm currently running 8.04 LTS on one hard drive and have a 2nd larger one that I'd like to install both Ubuntu 8.10 and Fedora 10 on.

Of course I'd like to be able to boot to either of the three distros so before I begin with the installation of either of the latter two, I'm looking for advice. Below is the fdisk report of my system as it is currently:

> root@Linux-DT:/home/scottw# /sbin/fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49394939

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x962f559d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1494    12000523+  83  Linux
/dev/sdb2           14645       15017     2996122+  82  Linux swap / Solaris
/dev/sdb3            1495       14644   105627375   83  Linux

Partition table entries are not in disk order


Keeping in mind that the two newer distros will go onto the larger drive (160), what would be my best bet for a successful installation?

Thanks!

---

### Post by cariboo on 2008-11-27
It shouldn't make any difference what order you install the OSs. The one thing to keep in mind is that last installation will be where grub will be setup and used.

Jim

---

