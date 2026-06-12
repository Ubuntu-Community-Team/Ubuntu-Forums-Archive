---
title: "Resizing Ubuntu partition"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2014-09-04
Hello everybody,

I would like to increase Ubuntu partition, I have a free partition (/dev/sda5 NEW VOLUME), and I would like to add it into Ubuntu partition (/dev/sda6), how can I perform this operation?

It is mentionned /dev/sda3/ 42GB, which is the total of both partitions, what is the next step?


[CENTER][IMG]http://s13.postimg.org/um8bv26ev/Free.png[/IMG]


[/CENTER]
Thanks in advance

---

### Post by yancek on 2014-09-04
Do not do this from GParted on the installed Ubuntu, use the Ubuntu installation medium which has GParted or a separate bootable GParted Disk.  The link below is to a detailed tutorial on GParted and it would be useful to read it.  Increasing the size of a partition is generally done by adding contiguous unallocated space and sda5 appears to be contiguous.  You can verify that with the output of the fdisk -l command.  Unmount sda5, delete it creating free space.  It doesn't appear you have much or any data on sda5 but if you do, move it first.  Then unmount sda6 by selecting that option from the Partition tab, then click that tab (Partition) again and select resize and the size.  The bottom part of the window will show what will be done and if it looks correct, click Apply, the check mark just below the Partition tab.

Backup all important data any time you are changing partition, before you do anything.

---

### Post by alfirdaous on 2014-09-05
The fdisk -l does NOT output anything

I could not see any link on your thread

The screenshot taken is from main Ubuntu, but I will use Ubuntu Live USB to do the partition

---

### Post by alfirdaous on 2014-09-05
I did the partition resize, but while I rebooted, I've got this error:

```

Error: no such partition
grub rescue >

```

---

### Post by alfirdaous on 2014-09-05
this is the result of fdisk -l

```

$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x347bad10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   192890879    96445408+   7  HPFS/NTFS/exFAT
/dev/sda2       192890880   200703379     3906250   82  Linux swap / Solaris
/dev/sda3       200703998   289146879    44221441    f  W95 Ext'd (LBA)
/dev/sda4       289146880   312571903    11712512    7  HPFS/NTFS/exFAT
/dev/sda5       200706048   289146879    44220416   83  Linux

Disk /dev/sdb: 15.6 GB, 15632171008 bytes
129 heads, 20 sectors/track, 11833 cylinders, total 30531584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         256    30531583    15265664    c  W95 FAT32 (LBA)

```

---

### Post by kansasnoob on 2014-09-05
Post a new screenshot of Gparted.

---

### Post by alfirdaous on 2014-09-05
I am using a Live USB, and the screenshot does NOT work, I took a screenshot with camera:

[IMG]http://s30.postimg.org/56vvon89b/image.jpg[/IMG]

---

### Post by yancek on 2014-09-05
Here's the link I forgot to post earlier.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by alfirdaous on 2014-09-05
Thanks yancek, I will check the link

---

