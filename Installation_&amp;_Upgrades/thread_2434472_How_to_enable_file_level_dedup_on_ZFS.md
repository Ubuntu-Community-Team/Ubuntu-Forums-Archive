---
title: "How to enable file level dedup on ZFS?"
date: 2020-01-06
forum: Installation &amp; Upgrades
---

### Post by dwater on 2020-01-06
I want to have a play with ZFS's debuplication, but want it on a file-level as described on this page:

[https://blogs.oracle.com/bonwick/zfs-deduplication-v2](https://blogs.oracle.com/bonwick/zfs-deduplication-v2)

I can't see any mention of it in the man pages though :/

---

### Post by Holger_Gehrke on 2020-01-06
Please reread the last paragraph of the part under the heading "What to dedup:  Files, blocks, or bytes?" in the article you link to. It clearly states: "ZFS provides block-level deduplication because this is the finest granularity that makes sense for a general-purpose storage system.". This agrees with all other articles on deduplication on zfs I can find.

Holger

---

### Post by dwater on 2020-01-06
> **Holger_Gehrke said:**
> Please reread the last paragraph of the part under the heading "What to dedup:  Files, blocks, or bytes?" in the article you link to. It clearly states: "ZFS provides block-level deduplication because this is the finest granularity that makes sense for a general-purpose storage system.". This agrees with all other articles on deduplication on zfs I can find.

Holger

Ah, yes, indeed. I read it, but didn't realise that it meant *only* block level, but I suppose it can be read that way. It's a bit of a shame, imo, but hey ho.

While you're here, how to tell it is working?

I tried to copy a large file to another one with a different name, and it still took ages and df/du still say it has used up double the space, if you get what I mean.

---

