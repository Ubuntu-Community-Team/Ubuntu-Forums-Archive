---
title: "Partition with no file system"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by jerim79 on 2012-05-19
I am trying to get DRBD setup on Ubuntu Server 12.04. The documentation doesn't really make it clear, but I believe it is best to install DRBD first on a partition and then format the partition with a file system after DRBD is installed. 

I have existing partitions with ext4 file system, but I can't seem to take the file system off without deleting the partition. With the file system on the partition, DRBD keeps complaining that the partition has no free space for the meta-data.

How do I create a partition without a file system? It would be great if I could setup partitions in the Ubuntu installer during partitioning.

---

### Post by 2F4U on 2012-05-19
The command line tool parted will be able to do that for you.

[http://www.thegeekstuff.com/2011/09/parted-command-examples/](http://www.thegeekstuff.com/2011/09/parted-command-examples/)

---

### Post by jerim79 on 2012-05-19
Thank you for the response. After a lot of trial and error I was able to get it working. I was able to use LVM to create a blank LV. I was able to get DRBD to work finally.

---

