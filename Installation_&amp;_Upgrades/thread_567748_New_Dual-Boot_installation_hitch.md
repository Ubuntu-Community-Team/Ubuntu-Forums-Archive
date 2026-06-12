---
title: "New Dual-Boot installation hitch"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by osiris2258 on 2007-10-04
I just added Ubuntu to my WIndows XP box. Most things are working fine, however there appears to be a problem with the file system. In gparted, the partitions show up as they should, but they can't be resized (the ubuntu install grew one of the windows partitions to twice it's original size, so Linux is in a smaller partition than intended); the message I receive is "check filesystem on /dev/sdc3 for errors and (if possible) fix them". In Windows, Partition magic reports the entire drive with the linux partitions on it (contains linux + 2 NTFS partitions) as "BAD". 

anybody have a clue how to fix these? both OS can see inside the partitions no problem, but this is bound to be an issue sooner or later, and also the linux partition is really small now.:(

---

