---
title: "growing a partion???"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by moose4204l on 2009-11-28
i was dual booting. I had ubuntu on 1 and windows on another. I put in the livecd and deleted the windows one. if i grow my ubuntu partition, will that mess up my data on that partition?

---

### Post by seeker5528 on 2009-11-28
There is never a guarantee that something won't get messed up, so doing a backup of the stuff you really care about is always suggested.

Having said that, unless there is a problem during the resize, the data should be fine afterwards.

If your Ubuntu partition was the first partition and Gparted just have to extend it, there is a little less risk. If your Windows partition was the first partition, then Gparted has to first move everything to the beginning of the drive, then extend the partition, so a little more risky.

Also when you do these types of operations Gparted has a tendency to want to number the partitions based on their order on the disk in some situations, so if both partitions were primary partitions and your Ubuntu partition was the second partition, Gparted may decide to make it partition 1 if there is not another partition that has that number, which could affect Grub entries, the stuff that uses UUIDs (fstab for example) should be fine. 

Later, Seeker

---

