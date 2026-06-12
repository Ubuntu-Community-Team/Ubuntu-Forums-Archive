---
title: "ntfs partition"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by prem1er on 2007-05-11
I have a 'backup' partition that came pre partitioned on my computer.  I decided to use this space to install Ubuntu.  It is an ntfs partition.  When I tried to install Ubuntu using the install option I didn't know what to do on the partition option.  It asked me to create a root directory on the partition I wished to install on.  What do I do?

---

### Post by bukwirm on 2007-05-11
You can't install Ubuntu on an NTFS partition. You'll need to:

1. manually edit the partitions
2. delete the NTFS partition you want to install Ubuntu on
3. then format the newly created free space as ext3. 

Then you can create the root directory on that partition. [This]("https://help.ubuntu.com/community/GraphicalInstall") provides a little more information.

IMPORTANT: Deleting a partition erases ALL data on that partition - be careful!

Update: [A little more info on partitioning]("http://www.psychocats.net/ubuntu/partitioning").

---

### Post by prem1er on 2007-05-11
Thank you.  I just deleted the partition using PartitionMagic (cause I was comfortable with it).  I'm currently formatting to ext3.  Thanks again.

---

### Post by prem1er on 2007-05-11
What is the difference between a Logical Partition and a Primary.  And which one should the ext3 be?

---

### Post by bukwirm on 2007-05-11
[Explanation of partitions]("http://www.pcguide.com/ref/hdd/file/structPartitions-c.html").

It probably doesn't matter weather the ext3 partition is primary or logical.

---

