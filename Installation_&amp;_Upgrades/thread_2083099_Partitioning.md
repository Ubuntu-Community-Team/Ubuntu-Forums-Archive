---
title: "Partitioning"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-11-11
I have read the gparted tutorial {thank's oldfred} and a lot of other posts re; partitions.
    If i am understanding it right i now have an extended partition equal to my entire HDD
with 3 logical partitions within it.
  When i install the next OS i create another logical partition within the unallocated space,
and install to that, correct?
    What should i use as mount point, for it and subsequent partitions ?  Since i can't use a
mount point already in use.
     Does it matter that swap is at the end of the disk?
Screenshot attached.                                                          Thank you.

---

### Post by darkod on 2012-11-11
Since the unallocated space is inside the extended partition, you can only create logical partitions from it.

If you plan to install more linux distros, the mount point of the root partition will again be /. Don't let it confuse, all linux distros need the / mount point, the OS knows which one is its root partition.

Since only one OS is running at any time, there will be no "conflict" with the other / partitions (mount points).
The swap partition can be used by all linux distros, there is no issue about that and again, since only one OS is running at any time, only one OS is actually using it at that time.

---

### Post by offgridguy on 2012-11-11
Thank you darkod;  that helps.

---

