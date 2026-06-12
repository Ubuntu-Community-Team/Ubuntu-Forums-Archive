---
title: "Partitioner cannot write to device"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by roadkill on 2008-10-23
I've just put together a new PC with an E8500 Core 2 Duo, GA-X48-DS4 motherboard and a 750 Gb Western Digital Greenpower drive.  

I've installed Win XP 32 (don't want the hassle of dealing with drivers for XP 64 or Vista) in preparation to giving most of the disk over to an Ubuntu 8.04 64 partition.  (The PC has 8 Gb RAM.)  However, when I attempt to repartition the HDD, I get the error "partitioner is unable to write to device".

Is there a way I can fix this?  Would it help to partition the drive using Partition Magic and then run the live CD?

---

### Post by didac on 2008-10-23
Try partitioning from inside Windows if you didn't use the whole hard disk.

---

### Post by roadkill on 2008-10-24
That did the trick - I partitioned from within Windows using Partition Majic, and created ext3 filesystems in the new partitions.  Ubuntu went onto them without issue.

---

