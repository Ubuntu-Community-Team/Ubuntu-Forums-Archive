---
title: "Using Part of NTFS Partition for Gutsy"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by clar2391 on 2007-10-03
In the past, when I've installed Ubuntu 7.04 on an existing NTFS drive, the GUI installation would offer several options, such as Use Entire Disk, Use Free Space on Disk, etc.  When I install Gutsy, the GUI only offers to use the entire disk, with no other options available.  I guess that I could manually partition the drive, but is there any way to enable the option to use the free space like 7.04 use to?  It's a 120GB drive and only about 30GB are being used by VISTA currently.

---

### Post by maybeway36 on 2007-10-03
Use Vista's built-in tools to resize the partition, then Gutsy will (hopefully) let you use the free space.

---

### Post by dabl on 2007-10-03
maybeway36 is correct -- the advice (and I haven't actually done it myself) is to use Vista's partitioner to shrink Vista.

There's more, though.

First, if you want more visibility and control over where things go, you may want to use the Alternate Install CD, either 64-bit or 32-bit, as applicable.  Although it gets called the "text" installer (it's actually VGA character mode), it has considerably more options for choosing where the filesystem pieces go, versus the Live CD.

Second, if you think this might be more than a short-term experiment, you might want to consider seriously making a GParted Live CD, and using that for the partitioning work in advance of booting the Alternate Install CD.  Why?  Because you might want 3 partitions for *buntu ("/", "/home", and "swap"), and Vista is already using 2, and that makes 5, which is one more than the maximum number of primary partitions allowed on a hard drive.  Consequently, you might need to make one of your partitions an extended partition, and then make 2 logical partitions ("/" and "/home") within it, leaving the fourth primary partition for "swap".

GParted ISO images are on SourceForge here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:)

---

