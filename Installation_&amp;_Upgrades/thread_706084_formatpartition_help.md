---
title: "format/partition help"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by fast eddie on 2008-02-24
I have put in a 2nd HDD (500G) to go with the 300G I already have in but I am having trouble getting the 2nd HDD mounted.

I get this error when I run sudo fdisk -l

[root@serverSB3server ~]# sudo fdisk -l

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 10 80293+ 83 Linux
/dev/hdc2 11 75 522112+ 82 Linux swap
/dev/hdc3 76 36483 292447260 83 Linux

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdd doesn't contain a valid partition table

Can someone explain what I am doing wrong and how I can get it to
work.

Thanks for your help

---

### Post by toa on 2008-02-24
> **fast eddie said:**
> I have put in a 2nd HDD (500G) to go with the 300G I already have in but I am having trouble getting the 2nd HDD mounted.

I get this error when I run sudo fdisk -l

[root@serverSB3server ~]# sudo fdisk -l

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 10 80293+ 83 Linux
/dev/hdc2 11 75 522112+ 82 Linux swap
/dev/hdc3 76 36483 292447260 83 Linux

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdd doesn't contain a valid partition table

Can someone explain what I am doing wrong and how I can get it to
work.

Thanks for your help

Fdisk didnt find any recognised partions on the Drive, which you said its a new drive, you need to format the partition and create partitions.

Try QtParted utility.

---

### Post by fast eddie on 2008-02-24
I think I have done it. Is this what the command sudo fdisk -l should show if all the disks are partitioned and mounted correctly:

[root@serverSB3server ~]# sudo fdisk -l

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          10       80293+  83  Linux
/dev/hdc2              11          75      522112+  82  Linux swap
/dev/hdc3              76       36483   292447260   83  Linux

Disk /dev/hdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       60801   488384001   83  Linux

cheers

---

### Post by zvacet on 2008-02-24
You see difference now.

---

