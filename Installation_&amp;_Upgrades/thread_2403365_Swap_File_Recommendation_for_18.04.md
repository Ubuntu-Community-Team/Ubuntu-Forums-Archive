---
title: "Swap File Recommendation for 18.04"
date: 2018-10-10
forum: Installation &amp; Upgrades
---

### Post by feartheterrapin on 2018-10-10
I recently upgraded from 16.04 to 18.04 with a fresh install.  My system has 16GB RAM.  Under 16.04 I had a swap partition of 8GB on the same disk as root that was used.  With the 18.04 installation, the entire disk is only the boot partition.  The swap is a 2GB file “”swapfile” in root.  Considering 16.04 required 8GB, is 2GB sufficient for 18.04?  Is there any advantage of using a file vice a separate partition that 16.04 used?

---

### Post by QIII on 2018-10-10
The old notions about the amount of swap space required are antiquated.  They came from the days when RAM was expensive and little was available on a system.

With 16GB available to you, any swap at all may be entirely unnecessary.  I stopped using swap at all when I started building systems with 8GB or more of RAM.  At 32 and 64GB on my home systems these days, I just don't bother.

The swap file has replaced swap as a partition in any case.  I wouldn't worry about it in the least.

---

### Post by feartheterrapin on 2018-10-10
Thanks!

---

### Post by Tadaen_Sylvermane on 2018-10-11
I know on Windows some things expect swap or virtual memory. I don't know if some linux apps are the same. I keep a 2gb swap just in case on every system I install.

For what it's worth, I've never seen my swap being used as per conky though.

---

