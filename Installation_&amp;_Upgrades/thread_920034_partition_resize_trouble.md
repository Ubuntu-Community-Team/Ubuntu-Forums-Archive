---
title: "partition resize trouble"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by JCGuitarist on 2008-09-14
hi, i am trying to install Ubuntu 8.04.1, i have windows xp already installed on a 60 gb hd, i am trying to dual boot and am running in to some issues. to make the install go faster i have inserted a 512mb swap space using partition magic 8, everything loads fine for the first few parts of the install, but when it asks me to prepare disk space i give ubuntu 15 gb, after i click ok to resize the partition it spins up the cd and looks as if it is going to work, it is reading something CONSTANTLY and the hd light blinks in unison with the cd light, i have no progress bar, no cursor, no sign that it is doing anything, it has been sitting in the same screen for a little over 2 hours now.

Is something wrong, is it really doing something? i am about to give up altogether.

Please any help would be useful.

---

### Post by Sef on 2008-09-14
> i have inserted a 512mb swap space using partition magic 8

Partition Magic and GNU/Linux tend not to work well together.  Redo the partitions with GParted which is on the Live and alternate CDs.

---

