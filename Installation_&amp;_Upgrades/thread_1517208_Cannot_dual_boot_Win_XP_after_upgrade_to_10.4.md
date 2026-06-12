---
title: "Cannot dual boot Win XP after upgrade to 10.4"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by deepblue80 on 2010-06-24
All
My excitement after upgrading to 10.4 disappeared as I could not dual boot into Win XP!! I still get the plain splash menu which gives me options to boot with Linux Kernel or win XP. when I chose Win XP it just goes blank and comes back with the same menu till i opt to boot with Ubuntu!! Any clues? I have attached the disk utility screenshot to give you an idea of my system. I have a 250 GB SATA HDD, 82 GB ATA and a 1 TB USB drive (for data only). I can still see my data which is a relief.

Thank you !!

---

### Post by darkod on 2010-06-24
You probably installed grub2 on the XP partition, /dev/sdb1. Use this procedure to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

So, you need to repair partition #1 on disk /dev/sdb.

---

