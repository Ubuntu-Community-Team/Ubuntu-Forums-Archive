---
title: "partition table change"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by htakai on 2007-11-15
I am installing Ubuntu 7.10 on a server with 7 Tbytes of RAID 5. I am using parted to create the partition table, etc....   So everything works great and I can mount /dev/sdb1 without a problem and I see the entire disk. 

NOW, when I reboot the system the partition is GONE. I looked at 

/proc/partitions and I can see that the partition size has changed **magically**. Is this a kernel problem? Has anybody seen this??


Thanks for any Help.   Helio

---

