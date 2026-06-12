---
title: "Ubuntu 5.10 install prob"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by mushin on 2006-06-21
Greets-   HP Pavilion 800MHz P3 laptop 512M RAM 100G HD.  2 partitions using System Commander 7.  20G XP Pro partition & 10G partition set for Ubuntu.  CD boots & gets to format of 10G space then barfs claiming no valid partition to install.  Help!  Ex-online computer tech help & pc box assembler/toubleshooter.  Not computer stupid but Linux gnuby (:wink: ).
Suggestions/advice?
Thanx.

_mushin_

---

### Post by zxee on 2006-06-21
You may need to open a shell (Alt+Ctrl+F1) and use cfdisk (just type cfdisk /dev/hda) to partition your hard drive. Are you sure that the partition is 10GB and are you selecting the correct partition during the install? Those are easy mistakes to make. If everything is as you say I don't know why the breezy installer can't find the partition you've set up.

---

