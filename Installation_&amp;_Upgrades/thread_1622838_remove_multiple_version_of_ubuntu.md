---
title: "remove multiple version of ubuntu"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by jlal on 2010-11-16
I have a 1 tera byte disk with windows xp nad a 120gb disk with ubuntu 7.10. I used install CD to install 10.04.

Now two versions of ubuntu are running and is creating confusion. How to remove the old version?

---

### Post by deconstrained on 2010-11-16
The main idea is to answer these two questions:

1. Which disk/partition is 10.04 installed on?
2. Which disk/partition is 7.10 installed on?

'sudo fdisk -l /dev/sd[a-z] /dev/hd[a-z]' should spit out a list of your disks and partitions. Also, take a look at /etc/fstab while booted in 10.04. Those two steps may give you an idea of where everything is. Reformat/delete the partition with 7.10 in it, and then re-generate your grub config to reflect the changes. For more details:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by jlal on 2010-11-20
fdisk details:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6c9c003

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497      121600   771955380    f  W95 Ext'd (LBA)
/dev/sda5           25497       57367   256003776    7  HPFS/NTFS
/dev/sda6           57368       89238   256003776    7  HPFS/NTFS
/dev/sda7           89239      121600   259947733+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000245b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14034   112722944   83  Linux
/dev/sdb2           14034       14594     4495361    5  Extended
/dev/sdb5           14034       14594     4495360   82  Linux swap / Solaris

/etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b0e78230-7a3b-483c-8332-080994b16a97 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by coffeecat on 2010-11-20
You have only one Linux root partition on sdb1. What makes you think you have two versions of Ubuntu? Are there several entries in the grub menu? These are likely normal and recovery options, and if you have more than one kernel after a kernel upgrade, two entries (normal and recovery) for each kernel.

---

