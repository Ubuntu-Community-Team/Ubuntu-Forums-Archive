---
title: "[SOLVED] ReiserFS or ext3FS?"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2006-06-26
I want to install Ubuntu 6.06 Release on a computer where currently is installed Libranet     LN3.0. For the LN installation I chose the Reiser File System when partitioning my hard drive. Can somebody tell me what is the better choice for the Ubuntu installation, ReiserFS or ext3FS?
Juergen

---

### Post by sbergman27 on 2006-06-26
Ext3.  You just can't beat ext3 for solid reliability.  It gives greater integrity guarantees than most journalling filesystems and does it by default.  I believe that reiser3, to its credit, also makes those guarantees, though I'm not sure if you get them by default.

In the event of curruption due to hardware malfunction (as opposed to power failure), your chances of recovering your data are better than with reiser3.  reiserfsck is still not really all that mature, and is handicapped by the fact that so much is allocated dynamically in that fs.  Ext3 is, perhaps, less exciting.  But its fsck is the result of many years of fixing little gotchas, and benefits from at least knowing exactly where more things would be after a crash than resierfsck does.

Unless you are working with zillions of little files, data integrity is not that important, and speed is paramount, go with the default ext3.

---

### Post by Cariboo1938 on 2008-02-19
> **sbergman27 said:**
> Ext3.  You just can't beat ext3 for solid reliability....
Unless you are working with zillions of little files, data integrity is not that important, and speed is paramount, go with the default ext3.

Thank you sbergman, I stick to ext3...Case closed!

---

