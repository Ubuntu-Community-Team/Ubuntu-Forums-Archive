---
title: "Ubuntu 10.10 installation can't see either windows or hard disk patitions"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by osm3000 on 2010-11-09
Hi,

I'm trying to install Ubuntu 10.10 64-bit on my laptop HP pavilion 3046ee . When I reach the partition part , it doesn't detect the Windows 7 os , and doesn't detect any hard disk partitions ( it sees the whole hard disk as one unallocated partition ).
I faced the same problem when I tried Ubuntu 10.04 LTS.

I'll appreciate any help

---

### Post by ajgreeny on 2010-11-09
More hardware info please.

Is this a raid setup, & what is on the disk at the moment?  Try running ```
sudo fdisk -l 
```(that's a lower case L at the end, not number 1) from the live CD/USB and post the output back here.

---

