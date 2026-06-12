---
title: "not able to format ubuntu using win7 disk"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by bhaskar202 on 2012-01-06
i m using ubuntu... i want to format ubuntu and want to install window 7. i m not able to format ubuntu partition using window 7 installation disk... wat should i do?

---

### Post by ottosykora on 2012-01-06
use gparted from an ubuntu life system or some other life system like partedmagic.com or similar and delete the partition from there. 
Then you can set up a partition from the windows gui tool.

---

### Post by efflandt on 2012-01-06
If you still have a working system to burn iso to CD or put iso on USB, you could use **gparted live** to remove partitions [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or of course you could use **gparted** from Ubuntu install CD or bootable USB.  You just cannot use gparted to remove partitions from the same system it is running from.
[]("http://gparted.sourceforge.net/livecd.php")

---

### Post by darkod on 2012-01-06
I haven't tried it but I think with windows you first need to delete the partitions (if that is what you want) and create new ntfs partitions with the size(s) you want.

It might not be able to simply format the existing linux partitions because it can't read them correctly.

---

