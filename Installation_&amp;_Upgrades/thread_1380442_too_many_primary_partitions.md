---
title: "too many primary partitions?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2010-01-13
I'm trying to get a dual boot set up for vista and 9.10

I already have 3 logical partitions

```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1966    15728640    7  HPFS/NTFS
/dev/sda3   *        1966       78071   611315712+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```


So I can make 1 more primary partion but after that no more! see screen shot

my plan was to make 3 logical, root, home, swap.

It does let me make 3 logical, but i don't know if i can use them?

im on a live CD now.

---

### Post by darkod on 2010-01-13
You have 3 primary out of total 4 partitions. Yes, you can create 3 more logical inside 1 extended, and that will fit into 4 partitions limit.

Just create the first partition as logical, and keep adding them as logical, it will create them automatically within one extended.

---

