---
title: "Replacing 8.10 Partition with 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by DaftPyramid on 2010-04-30
I am dual booting Windows Vista and Ubuntu 8.10. Trying to replace 8.10 with 10.04 while keeping the Vista partition. The partition manager is confusing and won't let me fully replace 8.10. Please help.

---

### Post by Mercury_Alpha on 2010-04-30
You'll need to choose the option to manually partition, if you want to replace 8.10 but keep Vista. Otherwise, the installer will attempt to put 10.04 alongside whatever else is on the hard drive; it defaults to the least destructive solution.

The manual partition screen will not have your current root partition labeled as such. Your current partitions will instead be identified as SDA1, SDA2, and so forth. You will have to identify the partition whose size and file system type (EXT3, EXT4, NTFS) matches that of the one that you want to delete. If you do not know its size or file system type, you will need to boot the LiveCD into desktop mode (rather than installer mode), open up GParted, and determine from there.

---

### Post by DaftPyramid on 2010-04-30
Okay, the manual wizard let me "delete" the 8.10 partition. Now how do I choose to install the 10.04 partition now?

---

