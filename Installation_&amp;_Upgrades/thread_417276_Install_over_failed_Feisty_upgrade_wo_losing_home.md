---
title: "Install over failed Feisty upgrade w/o losing /home?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by paullyjunge on 2007-04-21
My Feisty upgrade failed, and now my computer will not fully boot.  It gets the the fsck portion but then hangs there.  

Is there a way to install a fresh Feisty on my computer without losing any of my /home?  And no, /home is not on its own partition, sadly....   Anyone have any suggestions/solutions?  

thanks,
paul

---

### Post by Cyraan on 2007-04-21
If you have the free space, you could fire up gparted on the livecd, carve out a new partition somewhere.  Then mount the partitions and copy your files there, then when you go to reinstall, you can use it as a /home partition.

---

