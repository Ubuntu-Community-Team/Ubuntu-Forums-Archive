---
title: "Will Ubuntu auto partition my Vista drive?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by renshao on 2007-08-18
I'v got a PC which I have Windows Vista installed. Vista partioned all my HDD space to one drive which is NTFS. I think Ubuntu has wizard to reduce the NTFS partition and auto setup dual boot for me, right?

I've done this in XP but not sure about Vista, just want to get someone to confirm it, thanks

---

### Post by merlinus on 2007-08-18
You will need to use vista's disk manager to shrink its partition.  Beforehand, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after ubuntu install), and defrag several times.

Then the ubuntu partitioner can use the freed-up space, and set up a dual-boot system.

-merlin

---

