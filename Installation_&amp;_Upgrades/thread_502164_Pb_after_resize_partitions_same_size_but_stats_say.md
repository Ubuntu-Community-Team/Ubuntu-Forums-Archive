---
title: "Pb after resize partitions: same size but stats say the inverse"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by zoun on 2007-07-16
Hello,
 I had three partitions on a 80Gb drive:[LIST]
[*]50 /win
[*]28 /linux
[*]2 /swap[/LIST]I have replaced Grub and deleted partition + resize of /win under a Live-cd session with Ubuntu 7.04

Just after the operation Gnome Partition Editor increases by 20Gb the used space of /win.
When I restart under /win under the partition editor I have one partition of 80Gb but when I look into the properties of the drive it's the stats of before
/win 50
/win used 40
/win free  10

My data seems ok but even after a CHKDSK I can't see the space gained by the resize.

It seems to be common for people who revert to the previous "system". The Gnome partition editor makes something wrong and Windows cannot read anymore the list of partitions correctly.

A solution?


Thanks a lot

---

### Post by zoun on 2007-07-16
Gparted corrupted my harddrive.
Qtparted reads correctly the current state and a resize down resize up of 1GB (just to perform a basic operation in order to oblidge qtparted to rewrite the table) has corrected everything.

Lesson: Never use gparted but qtparted instead

---

