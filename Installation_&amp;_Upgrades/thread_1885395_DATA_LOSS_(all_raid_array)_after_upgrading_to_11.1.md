---
title: "DATA LOSS (all raid array) after upgrading to 11.10"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by yanaek on 2011-11-23
I think I lost all my (very important) data from MDADM/LVM raid array after upgrading to 11.10.
I had 4 x 1TB disks in mdadm as one PhysicalVolume for LVM.

After upgrade and reboot I was notified, that home and  other directories, which were on raid, are not readable and need to be fsck'ed.

Fsck was unsuccessful so i rebooted and checked mdadm and I realized that in mdadm two of four disks have no partition, it looked like this:
/dev/sdb
/dev/sdc1
/dev/sdd1
/dev/sde

fdisk /dev/sdb and sde showed errors in partition table (invalid flag 0x00...)

I re-created partitions (1) on sdb and sde and set up fd  flag again. Then restored volume group config from LVM but seems like all data is lost.

How can it be possible that during upgrade I got errors on two of my raid 5 disks???

---

### Post by yanaek on 2011-11-28
Seems like there may be two reasons why I lost my raid array during upgrade.
I remember that in console, when grub was upgraded or just initramfs re-created, there were messages like here [http://comments.gmane.org/gmane.comp.boot-loaders.grub.devel/17669](http://comments.gmane.org/gmane.comp.boot-loaders.grub.devel/17669)  (found two disks with the index X for raid md0)
and also something about wrong lvm metadata.

Currently I lost all data since last backup, last year, and this is a catastrophy. You should be extra careful when upgrading system with mdadm and lvm2 to ubuntu 11.10

This issue looks similar (lost partitions in mdadm) [http://ubuntuforums.org/showthread.php?t=1736742](http://ubuntuforums.org/showthread.php?t=1736742)

---

