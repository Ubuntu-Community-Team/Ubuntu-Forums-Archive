---
title: "alternate install cd extended partition question"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by entropy1 on 2009-11-28
I am trying to use the 9.04 alternate install cd to set up a dual boot system.  The system has 2 primary partitions used by XP, and I have used manual partitioning to create free space.  How do I make the free space into an **_extended_** partition inside which I can put a swap partition, a /home partition, and a / partition?

Solution:  I found that by selecting the type of partition for swap, /home, and / to be "logical", each one was automatically put into an extended partition.

---

### Post by Bartender on 2009-11-28
Entropy, this is one of the reasons why I like to set up my partitions beforehand with a GParted LiveCD.  The installer partitioner doesn't even let you build an extended.  You just have to build logical partitions and hope for the best.  I think that's goofy and unnecessarily confusing.

---

