---
title: "ubuntu partitions"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by ddimit on 2012-04-26
hello guys 
im unable to install ubuntu just because it does not recognize windows 7
i want to install it alongside windows 7 but the installation does not find any partitions
the last time i tried to install it , it did not find any partitions and  i used a program you told me which shows all the partitions but it still  shows one whole partition
the last time i installed it on that partitions and it destroyed all my partitions and data
please tell me a working method to make it recognize windows 7
here are my partitions [IMG]http://i50.tinypic.com/2dhv3i9.png[/IMG]
i want to install it on 48.83 partition

---

### Post by darkod on 2012-04-26
It's not that it can't see win7. The thing is that you have the maximum of 4 partitions on the disk, so it can't create new one.
Delete that 48GB partition. Do not create partitions for linux in windows because it can't create linux partitions. Leave the space as unallocated (unpartitioned) and the install should go fine.

---

### Post by Mark Phelps on 2012-04-26
If you decide to go ahead with dual-boot, then use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

