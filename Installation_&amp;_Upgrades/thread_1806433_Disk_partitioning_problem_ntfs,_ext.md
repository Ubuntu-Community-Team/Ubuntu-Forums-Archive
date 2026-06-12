---
title: "Disk partitioning problem ntfs, ext"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by manolooo on 2011-07-17
I'm writing this post to help people that might find the same problem I had.

I began with a Windows machine that I wanted to move to Linux. The machine had 2 ntfs partitions: one for OS + programs (Disk C:) and the second one for data (Disk D:). 

I formatted Disk C. to ext 4 and installed Linux while pretending to keep Disk D as ntfs. This didn't work well. Although Linux can use both partitioning methods it seems they cannot be used in the same disk.

The result was that my machine got to a very high CPU load, it worked more or less correctly but CPU was at 100 % most of the time.

After I formatted the data partition (Disc D:) to ext4 it all changed and my computer started to run very, very smooth. Never forget to make a backup copy if you format a partition, if not you'll lose all data...

---

