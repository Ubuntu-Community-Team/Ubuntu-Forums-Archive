---
title: "gParted not allowing partition change"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by SCGhst1 on 2007-04-07
Hello everyone!

Something very weird happens with gParted...I start it up with root priviledges, my filesystem is Ext3, and it doesnt allow me to resize the my main partition, my reason for wanting to do this is because i was planning on a dual boot system with windows and wanted to keep ubuntu without having to reformat, install windows, then resize from the main ubuntu installer program, it takes too long. I cant very well unmount my  hard drive to resize it because everything would go blank...so i was wondering how would i go about resizing my hard drive

---

### Post by ndube on 2007-04-07
You can't resize a mounted partition and since the partition you need to resize is your /, you need to download the gparted live cd and boot from it. Then you should be able to resize your ext3.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

