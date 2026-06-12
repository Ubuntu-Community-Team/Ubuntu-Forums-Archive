---
title: "Unable to Boot Windows 7 - Dual Boot Ubuntu 14.04"
date: 2016-03-15
forum: Installation &amp; Upgrades
---

### Post by Flemm on 2016-03-15
Decided to give Ubuntu a serious go this time around. I used a live USB and manually setup the partitions (/, swap, /home). Before all that, I shrunk my windows partition. And was having a blast customizing Ubuntu and installing various packages, until a few days later when I decided to boot into Windows 7 to play some games. Then I got, "failure to boot windows . . . status 0ex000225 or something of that sort. Here's my boot-repair [report]("http://paste.ubuntu.com/15393231/"). Thanks!

---

### Post by oldfred on 2016-03-15
Did you backup Windows?

I see a recovery partition - sda1 which may totally erase drive & restore Windows and I see the small 100MB Windows boot partition - sda2.
But there is not a large NTFS partition that would have been main Windows install.
You have extended partition will all the logical partitions as Linux.

---

### Post by Flemm on 2016-03-15
Hey thanks for the reply! No, I never did a full backup, just backed up a few individual files here and there, which is no big deal. I'll just do a reinstall and play closer attention the next time around. Thanks again.

---

