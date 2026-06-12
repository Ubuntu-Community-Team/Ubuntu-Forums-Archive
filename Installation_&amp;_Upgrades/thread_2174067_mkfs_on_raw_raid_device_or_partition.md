---
title: "mkfs on raw raid device or partition"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by klausmedk on 2013-09-12
Hello

I have created an array (mdadm) called /dev/md0
Should I make a filesystem directly on that or should i first create a partition and then create a filesystem on the partition.
If I were to make a partition I would only require 1 partition anyway.

Is the answer the same when it comes to disks, e.g. /dev/sdd vs /dev/sdd1?

Regards
Klaus

---

### Post by SaturnusDJ on 2013-09-12
Partitions go on the array members.
Filesystem goes on the array.

Sometimes users use full disks as array members. You can read here why that's not a good idea: [http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473](http://ubuntuforums.org/showthread.php?t=2110658&p=12484473#post12484473)

---

### Post by klausmedk on 2013-09-13
Thank you for the reply.

Yes my memebers are partitions....for the reasons stated in the link you posted.

My question was only concerned on whether to create a partition on the array /dev/md0p1 or to create the file system directly on /dev/md0.

Your answer clearly says create filesystem directly on /dev/md0. 

But would there be situations where one would want to create partitions on the array?

//Klaus

---

### Post by SeijiSensei on 2013-09-13
I'm not sure you can partition an md device the same way you would a physical drive, but you can install [LVM]("https://wiki.ubuntu.com/Lvm") on top of the array instead.

Usually if I want, say, three differently-sized RAID devices, I partition the physical drives accordingly and create three separate md devices.  I'm pretty good at estimating how large / or /var needs to be, but if you underestimate the size you need, you're stuck with copying off the data from the arrays and repartitioning the drives.  LVM lets you adjust sizes after the face without repartitioning.

---

