---
title: "How to create partition &quot;table&quot; by fdisk?"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by Yunus Emre on 2008-10-24
Hi.
I'm using both Ubuntu 8.04 and Pardus 2008.1. Today while I'm running on Pardus 2008.1 I've made some mistaken changes - which is create partition table - on my partition table by GParted. Then it warned me, "This will erase all data on your disk." and I clicked "cancel."

A few hours later, I needed to restart Pardus. While restart I got a GRUB error 22. Then I've checked my partitions on Ubuntu live cd. There was nothing but an unformatted 250GB partition. I've googled it and learned that there is a chance of losing the partition table but not the data.

Here is my partition table, which I've printed after installation,

```
Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x084b084a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4292    34475458+   7  HPFS/NTFS
/dev/sda2            4293       30401   209720542+   f  W95 Ext'd (LBA)
/dev/sda5            4293       25240   168264778+   7  HPFS/NTFS
/dev/sda6           25241       27790    20482843+  83  Linux
/dev/sda7           27791       28039     2000061   82  Linux swap / Solaris
/dev/sda8           28040       30401    18972733+  83  Linux
```

And here is my question, how to create this partition again by using fdisk, or any program that you'll suggest?

---

### Post by logos34 on 2008-10-24
> **Yunus Emre said:**
> And here is my question, how to create this partition again by using fdisk, or any program that you'll suggest?

[**TestDisk**]("http://www.cgsecurity.org/wiki/TestDisk")

(See "[Current Partition Table Status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")", thru step 9)

good luck

*You'll need to boot from the ubuntu live cd and install it:

System>Admin>software sources>check **universe** repos

sudo apt-get install testdisk

sudo testdisk

---

### Post by Yunus Emre on 2008-10-24
Thanks, it worked! :)

---

