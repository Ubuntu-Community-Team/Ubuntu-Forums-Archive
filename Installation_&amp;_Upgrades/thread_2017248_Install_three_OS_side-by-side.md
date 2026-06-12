---
title: "Install three OS side-by-side"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by steveray100 on 2012-07-05
I know that you can have Windows and ubuntu side-by side and then choose which one you want at boot but can you install three?

---

### Post by Quackers on 2012-07-05
Yes, but you will likely need to have an extended partition and systems that can boot from a logical partition (inside an extended partition) - like Ubuntu, for instance.
This does not apply if you are using GUID Partitioning, as opposed to msdos partitioning (or MBR).
If using MBR make sure you do not exceed the maximum of 4 primary partitions (or 3 primary partitions plus an extended partition, which can hold almost as many logical partitions as you wish).

---

