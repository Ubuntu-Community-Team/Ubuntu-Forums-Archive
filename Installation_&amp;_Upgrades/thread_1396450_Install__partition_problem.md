---
title: "Install / partition problem"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Dimonchek on 2010-02-02
Hi. I'm trying to install Kubuntu from CD. On the 4-th step (Disk Setup) chose Manual. I have 4 partitions on my hd, but installer don't show me anything, except whole disk(sda)

---

### Post by oldfred on 2010-02-02
The MBR partition scheme only allows 4 partitions. You can have 4 primary partitions or 3 primary and one extended that can hold many more logical partitions.

If you have used all 4 primary you will have to delete one partition to allow installation or buy another hard drive.

You could backup one partition with data and then create the new logical and copy back the data. This all assumes you have lots of available space on your hard drive. Moving data around can be a slow process with gparted. You should have everything backed up.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by Dimonchek on 2010-02-02
I have only 2 primary partitions(for windows and linux).

But when i check it with TestDisk it shown me, that there are mistakes on it(numbers of cylinders, broken blocks). Trying to repair it.

---

