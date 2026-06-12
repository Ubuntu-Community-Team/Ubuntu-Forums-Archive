---
title: "doubt about the disks's organization"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by zerolink on 2007-06-30
I have Windows in the first partition, linux installation in the next partition (ext3), and swap partition in the last.

but the devices organize logically this way:

/dev/hdb1 -> NTFS -> Windows XP
/dev/hdb3 -> ext3 -> Ubuntu
/dev/hdb4 -> swap
_______


now, my questions are: ¿why it put the first hard drive (my only hard drive) in hdb instead hda?,
and ¿why it skips hdb2?


thx--

---

