---
title: "HELP! i lost everything :( (partitioning)"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by jacobxtyler on 2009-12-09
i was trying to install ubuntu, and i accidentally changed my ntfs partition with my windows 7 stuff to ext4 and now windows wont boot and i cant get to it. what can i do?

---

### Post by raymondh on 2009-12-09
> **jacobxtyler said:**
> i was trying to install ubuntu, and i accidentally changed my ntfs partition with my windows 7 stuff to ext4 and now windows wont boot and i cant get to it. what can i do?

If it reformatted from NTFS to ext4 ... sorry ...... reformat means it will rewrite clean said area/partition to the new format.   :(

---

### Post by jacobxtyler on 2009-12-09
so what your telling me is that everythings gone? :(

---

### Post by raymondh on 2009-12-09
> **jacobxtyler said:**
> so what your telling me is that everythings gone? :(

Are you using the liveCD?  Access a terminal and type

sudo fdisk -l

post back.  I want to make sure.  Did you proceed and reformat the win7 partition?  If yes, then you overwrote said partition by formatting (writing) a new file system/format.  That means you lost win7. Sorry.

---

