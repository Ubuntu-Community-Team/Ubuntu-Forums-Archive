---
title: "New install"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2010-07-31
Am trying to dual boot XP and Ubuntu.  Every time I try to install it picks on the raid disks (where all the data files are) rather than the partition on the main disk where the previous Ubuntu install is.  I cannot find a way of telling it where to install.  How do you do this?  Previously I've always used an alternate install iso to dictate where it will install but this will not boot despite using same method to burn the desktop iso that works but will not let me install where I want.

---

### Post by hyperAura on 2010-07-31
u can choose to do it manually and then u'll get all disks with all partitions.. If u can tell which disk has Ubuntu on it by the size, then u can choose to resize and partition to install win XP..

---

### Post by ajgreeny on 2010-07-31
At the partitioning page of the install choose the manual partitioning, then you can set the specific partitions you want for your setup.  Whilst you are at it, it could be worth looking at the possibility of a separate /home partition.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for details.  This page is also very useful for general info on installation whether you use a separate /home or not.

---

### Post by lift_test on 2010-07-31
> **ajgreeny said:**
> At the partitioning page of the install choose the manual partitioning, then you can set the specific partitions you want for your setup.  Whilst you are at it, it could be worth looking at the possibility of a separate /home partition.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for details.  This page is also very useful for general info on installation whether you use a separate /home or not.

I did try the manual option but it still only shows the raid disk, the primary hard disk is not visible.

---

### Post by lift_test on 2010-07-31
> **lift_test said:**
> I did try the manual option but it still only shows the raid disk, the primary hard disk is not visible.

It's very strange, I've downloaded again and burnt the alternate iso.  It now boots and starts OK but when I get to the disk set up it recognises the Sata raid array and the main Maxtor hard drive but will only want to use the whole hard drive and therefore overwrite Windows.  Why?

---

