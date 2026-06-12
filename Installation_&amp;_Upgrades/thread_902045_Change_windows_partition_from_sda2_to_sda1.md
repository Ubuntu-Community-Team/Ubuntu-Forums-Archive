---
title: "Change windows partition from sda2 to sda1"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by indianballer24 on 2008-08-26
I recently installed ubuntu and it changed my windows partition from sda1 to sdb1. How do I change it back to sda1?

---

### Post by Sef on 2008-08-27
With the Live CD:

System > Applications > Terminal

Copy and paste or type in this code:

```
sudo fdisk -l
``` Small L

Copy and paste the results here.

---

### Post by indianballer24 on 2008-08-27
Here is my fdisk -l. I don't mind having to delete the ubuntu and reinstall it later if I can make my windows (ntfs) partition sda1. Any help is appreciated. Also if anyone knows, why are there two ext3 partitions for ubuntu (sda1 and sda5) ? This is not from the live cd. I am currently on the Ubuntu system that is installed on the computer.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ce69ce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            5566        5643      626535   83  Linux
/dev/sda2   *           1        5565    44700831    7  HPFS/NTFS
/dev/sda3            5644        9729    32820795    5  Extended
/dev/sda5            5644        9555    31423108+  83  Linux
/dev/sda6            9556        9729     1397623+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

