---
title: "Guide for partitioning HDD for installation"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-16
Is there a guide to instruct newbies on best practices to create partitions during installation of Ubuntu?

I want to try installing on another PC using an "old" IDE 40GB disk.

Basically my friend showed me once that when creating 1st partition you use "/" which I assume it means to install the OS, so this is root. He told me to allocate 10GB for the OS.

Then he created a 2nd partition and use the "Swap" option and he allocated the rest of the HD, about 30GB.

I see some comments that one should also create a 3rd partition and use "/home".

Quick question: for a 40GB how many partitions and how would you use them?

I guess I'm looking for a guide that defines the various terminologies available in the drop down when creating the partitions using the live CD.

Thanks.

.

---

### Post by bluebyt on 2007-05-16
Here a great guide:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by geek2330 on 2007-05-16
Thanks, I actually found that link and another tutorial from this great site.

My only question left is what's the difference between choosing ext3 or ext2 from the drop down.

I created 1st partition as ext3 for /

Then I wonder if I use ext3 also for my /home partition.

---

### Post by UNIXnewbie on 2007-05-16
ext3 is basically the file system type.  ext3 is a newer version of ext2 so you would use ext3 for all of your working partitions.

In short, yes, you would use ext3 for your /home too.

---

