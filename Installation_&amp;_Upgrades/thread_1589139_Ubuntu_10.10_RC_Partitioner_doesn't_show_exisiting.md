---
title: "Ubuntu 10.10 RC Partitioner doesn't show exisiting partitions"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by lszanto on 2010-10-06
Hey,

I went to install the 10.10 RC yesterday but to my surprise when I got to the partitioning stage it showed up my drive as being blank, with no existing partitions.

Has anybody else had this issue? I'm not sure what to do as I had the same issue on the beta, I just assumed it would be fixed.

I have a 500GB Sata HDD and i'm running an AMD64 processor so the RC was the amd_64 version.

Any help would be much appreciated.

Thanks, lszanto

---

### Post by srs5694 on 2010-10-06
Chances are the problem is the one [described here.](http://www.rodsbooks.com/missing-parts/) If I'm right, although this is arguably a bug in libparted (which is the partitioning library used by the Ubuntu installer), it's triggered by a damaged partition table on your hard disk.

---

### Post by lszanto on 2010-10-07
Thanks, I will try this later :)

---

### Post by garvinrick4 on 2010-10-07
If nothing else works try this it seems to work a lot in this exact situation.
After booting cd:
```
sudo apt-get remove dmraid
```
Now install:

---

