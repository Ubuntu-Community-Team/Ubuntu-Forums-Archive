---
title: "dual boot 9.10 with debian lenny"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by swappo1 on 2009-12-06
Hello,

I have Debian 5.0 installed and I want to set up to dual boot with Ubuntu 9.10.  I'm not sure how to partition my drive.  Here is what I have for partitions:
/dev/sda
    /dev/sda1 Debian 6.5 GB ext 3
    /dev/sda5 swap 9.3 GB
    /dev/sda6 14GB ext3
    Free space 217GB

Using the livecd and custom partion screen, I created two new partitions with the free space for / and /home but then it said free space wasn't usable even though I had plenty of free space so I undid the partitions. When I created the two new partitions, I just added them.  I don't know if this was the right way to do it. How do I set up Ubuntu with 5-10 GB partition and a home partition with 10 GB and dual boot with Debian?  I still want to keep a lot of free space.  Thanks.

---

### Post by oldfred on 2009-12-06
You probably have your extended partition trapped between primary partitions so there is no more room to install. Normally you create 3 primary partitions first the the fourth is the extended for the rest of the drive and you can create essentially as many partitions as you want in the extended partition. 

You cannot really share /home with other linux so you may want to create a /data partition for all the files you may want to share. If you have all data in a separate partition /home becomes just the user settings and does not have to be separate as it is easy to back up for a new install.

---

