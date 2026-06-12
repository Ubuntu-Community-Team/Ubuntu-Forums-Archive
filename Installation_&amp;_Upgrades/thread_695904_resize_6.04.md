---
title: "resize 6.04"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2008-02-13
Have a ubuntu hd partitioned with 50g for 6.04 & ~3gig for the swap. Since ubuntu only uses ~3g would like to turn most of the unused space into an empty partition. Ran 7.04 livecd & started gparted. Asked it to resize the ext3 to 20g. Starts out & quickly says no can do. So what am i missing? TIA

---

### Post by taurus on 2008-02-13
What is the exact error message instead of no can do?  Make sure you don't mount the harddrive first before you try to resize it.

Perhaps GParted LiveCD works better.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by jtmedin on 2008-02-13
Got gparted livecd but it ended up as a command line program, unless i missed something when it was loading. So that was no help.
Downloaded 7.1 livecd & ran gparted which worked :-). Now if i can get the swap partition to move down also.

---

