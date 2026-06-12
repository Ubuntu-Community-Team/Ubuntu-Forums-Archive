---
title: "partition that win xp and ubuntu can write and read to"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Bartikky on 2007-06-11
Hi all, I was wondering what system file type I need that win xp and ubuntu can write and read to, is it fat32 or fat?

---

### Post by Catsworth on 2007-06-11
Win XP and Ubuntu should both be able to read/write from/to a FAT32 partition.

---

### Post by Bartikky on 2007-06-11
Thanks, Catsworth!
By the way, like your signature message, haha!

---

### Post by merlinus on 2007-06-11
My suggestion is to use ext3, which is far better than anything FAT.

Then install the appropriate drivers (ntfs-3g for ubuntu and ifs for windows), and you can read and write from both sides.

-merlin

---

