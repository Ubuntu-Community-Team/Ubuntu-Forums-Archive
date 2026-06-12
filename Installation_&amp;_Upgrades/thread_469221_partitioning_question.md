---
title: "partitioning question"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by kidob on 2007-06-09
I'll be installing Ubuntu in a couple days as a dual boot with XP and as I try to plan out my partitions I've come up with a few questions. I'm installing on a 40 GB HDD and I plan to devote at least 20 GB to Ubunto, maybe 25. I'm planning to create an extra /home partition of 10-15 GB. That being said, here are my questions:

--Should the partition I create for the /home directory be primary or logical? (right now there are no extra partitions on my drive, so there's no danger of exceeding any limits)

--Should I format the /home directory as ntfs or fat32?

--What's the difference between ntfs and ext3? I believe the main partition for ubuntu should be ext3, and the /home should be ntfs or fat32? But what's the difference?


I think that covers it. Once I get a sense for these distinctions I'll be ready to install with confidence!

---

### Post by merlinus on 2007-06-09
ext3 is for linux, ntfs is for windows.

But you can install drivers that will allow reading/writing to/from both file systems.

-merlin

---

### Post by kidob on 2007-06-09
thx merlin--so I should make the main directory a primary ext3, and then set up a logical partition, also ext3, as the /home? Or should both be primary? or does it not matter in the least whether the /home is logical or primary???

---

### Post by merlinus on 2007-06-09
It does not matter.  You can have 4 primaries, one of which can be an extended partition and can contain many logical partitions.

All partitions in Linux should be ext3.  There are other choices, but at present I believe this is the best.

-merlin

---

