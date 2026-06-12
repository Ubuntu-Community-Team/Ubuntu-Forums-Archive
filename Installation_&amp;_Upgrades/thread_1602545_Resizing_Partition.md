---
title: "Resizing Partition"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by shaikat on 2010-10-21
Hi all,

I am very new on Linux and also in Ubuntu. I have started to use Ubuntu 1 week ago. When I first install Ubuntu, I make the partition (Ext4) of 10 GB. I also make NTFS partition around it. Now actually I want to increase my partition size to 30 GB. I attack my disk status with a picture.

[IMG]http://img576.imageshack.us/img576/2606/diskpartition.png[/IMG]

I can delete the NTFS partition in the right side of Ext4 partition. So, please help me how can I do it. Is the any software available to resize the partition?

Thanks in advance. 

Shaikat

---

### Post by Fire_Chief on 2010-10-21
You can use GParted ([http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")) to make partition changes to the system if you like.

You will have to remove all the partitions to the right of the ext4 partition to expand it. Then recreate the partitions after it.

Cheers!

---

### Post by perspectoff on 2010-10-21
GParted is also available on the Ubuntu LiveCD. Boot into that LiveCD ("Try Ubuntu") and start GParted (System -> Administration -> GParted).

You don't have to delete or create anything.

Move the partitions (the 51 Gb extended partition and the 49 Gb NTFS partition) to the right until the 147 Gb free space is next to your 10 Gb ext4 partition. Then you can expand ("grow" or "resize") your ext4 partition so that it includes the free space, becoming a 157 Gb ext4 partition (or 30 Gb, or whatever you want).

---

### Post by shaikat on 2010-10-21
Thanks for the help. :)

---

### Post by srs5694 on 2010-10-22
I wrote a two-part piece ([Part 1](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html), [Part 2](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)) for IBM developerWorks on this topic a while ago. Part 1 is particularly likely to be useful to you. It describes the software and procedures in a little more detail. If you run into a stumbling block, post back with more details. A screen shot of the GParted window can be particularly helpful in such cases.

---

