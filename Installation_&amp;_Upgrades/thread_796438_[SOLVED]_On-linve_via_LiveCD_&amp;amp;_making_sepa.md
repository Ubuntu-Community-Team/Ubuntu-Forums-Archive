---
title: "[SOLVED] On-linve via LiveCD &amp;amp; making separate /home"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2008-05-16
I'm running HH LiveCD. 

I'm trying to follow Psychocat's instructions for putting /home on it's own partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I'm not using any NTFS, so the entire 320 gig (290 gig formatted) is Ubunutu. 

My problem is, when I resize/move I am not expanding the / partition to 15 gig, which is what I want. Then I'll add another partition for /home.

Also, when the HH was installed, GParted shows a approx. 2 gig "extended" partition, then the swap. Is the extended part of swap or unnecessary?

---

### Post by logos34 on 2008-05-16
The guided install usually puts swap on a logical partition.  An extended is just a wrapper for the partitions inside, but is separate in the sense that it has its own partition #.

Working from the live cd you should be trying to shrink / from its right border.  Then create the /home in freed space.

---

