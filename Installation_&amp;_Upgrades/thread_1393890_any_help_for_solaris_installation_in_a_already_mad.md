---
title: "any help for solaris installation in a already made partition ??"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2010-01-29
here is my current partition table

```
Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1642    13189333+   b  W95 FAT32
/dev/sdb2            1643       30401   231006667+   f  W95 Ext'd (LBA)
/dev/sdb5            1643        6128    36033763+  83  Linux
/dev/sdb6            6129        6329     1614501   82  Linux swap / Solaris
/dev/sdb7            6330       13406    56845971   83  Linux
/dev/sdb8           13407       19932    52420063+  83  Linux
/dev/sdb9           19933       25104    41544058+  83  Linux
/dev/sdb10          25105       27763    21358386    b  W95 FAT32
/dev/sdb11          27764       30401    21189703+  83  Linux

```

i want to install solaris in /dev/sdb10

installer disk partitioner selects entire extended partition .
how can i format and install opensolaris 2009 in the partition 10??
in the older ubuntu i thought i saw the gparted offered to format to solaris but now it is not giving such an option.

any help??

---

### Post by quixote on 2010-01-30
I was pretty sure I'd seen "Solaris" as a file system choice under fdisk, and according to [http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html) it is.  Oddly enough, it's designation is "82", same as linux-swap.  Weird.  Still, that implies you should be able to format a partition as solaris using fdisk, if gparted isn't doing it.

While I was checking to see if I remembered right, this site [http://docs.sun.com/app/docs/doc/819-2723/disksxadd-19036?a=view](http://docs.sun.com/app/docs/doc/819-2723/disksxadd-19036?a=view) also came up.  It looks like the usual Sun gobbledygook, but about two thirds of the way down they do have: "Example 13–2 x86: Creating a Solaris fdisk Partition While Preserving an Existing fdisk Partition."  Maybe that could be useful.

---

