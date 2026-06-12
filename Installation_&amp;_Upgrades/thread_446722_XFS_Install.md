---
title: "XFS Install"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by jb000001 on 2007-05-17
Good Day

How can i install ubuntu desktop with a custom formated root partition?

I created my partitions using cfdisk using the live cd
I then formatted the partitions from the command line and tried to install ubuntu

I have three partitions:

1) /boot     (100Mb, ext2) 
2) swap    (512Mb, swap)
3) /             (7GB, xfs)

I then formatted / with: mkfs.xfs -l size=64m /dev/sda3

Unfortunatly ubuntu insist on formatting the root before it would install.

Any Ideas?

---

