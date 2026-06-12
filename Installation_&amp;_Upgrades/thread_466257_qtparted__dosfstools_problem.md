---
title: "qtparted / dosfstools problem?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by maybeway36 on 2007-06-06
I seem to have a problem when making FAT32 partitions via QTParted. My FreeDOS floppy complained that "the partition type does not indicate LBA" but worked anyway. Windows XP also booted from the partition and did not give me any errors. It seems QTParted is using the partition type 0B (FAT32) rather than 0C (FAT32 w/ LBA.) I believe QTParted uses dosfstools to deal with FAT partitions, so I assume GParted will do the same thing. (I eventually used the DOS program ptedit.exe to change the type from 0B to 0C and FreeDOS stopped giving me the error.) Any idea why this happens, though?

EDIT: Never mind. The lba flag can be changed with GParted, which amounts to changing the partition type. Now I know I'll use GParted for making FAT32 partitions, especially since it's now on Knoppix.

---

