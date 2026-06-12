---
title: "Linux partitions - which to use?"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by bcsco on 2008-01-15
I have XP installed on a 60Gb Fat 32 partition. I installed Ubuntu 7.04 on a 6.5Gb ext2 partition. It seemed to run fine. Somewhere I read an ext3 partition is better, so I decided to upgrade to Ubuntu 7.10,changed the partition to ext3, and overwrote the partition with 7.10. My swap partition (ext2) is just under 1Gb. On boot, the screen remains blank for over 2 1/2 minutes until the mouse cursor appears. A very slow boot (Windows takes half the time to get to the desktop). This is far more time than version 7.04 took to boot on the ext2 partition. I've since gone back to a ext2 partition and version 7.04.

I'd like to reinstall 7.10 but am curious whether the change in partition from ext2 to ext3 partially caused the delay in booting. What type partition should I be using? What size would be best (I have room on my XP Fat32 partition so could resize that)? This is all new to me so I need some pretty explicit instructions. :confused:

---

### Post by dgray_from_dc on 2008-01-15
ext3 is ext2 with journaling added and is better.  For your swap partition, you should NOT be using ext2 that should be linux swap.  There is a special file system for swap.  If you somehow did manage to use an ext2 formatted partition for swap, that may be what caused your problem.

---

