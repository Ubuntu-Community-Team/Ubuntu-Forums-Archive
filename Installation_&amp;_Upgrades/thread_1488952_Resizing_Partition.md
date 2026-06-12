---
title: "Resizing Partition"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Tweep Cat on 2010-05-20
Hi, I am installing ubuntu on my Delete Inspiron laptop and after selecting "install them side by side" optio the window saying "Resizing partition..." on it has come up and just says 0%. I am partitioning so that ububtu has 100GB, but should it be taking this long - it's been about 25 mins. Is this normal?

---

### Post by Tweep Cat on 2010-05-20
Okay, it has been about an hour. Should I leave it or reboot?

---

### Post by srs5694 on 2010-05-20
Interrupting a partition resizing operation is *very* dangerous. The only item in your favor is that it's stuck at 0%. If that's *precisely* 0%, then by definition nothing's been done; however, if *any* on-disk data structures have been altered, chances are you'll have a hard time recovering data from that partition. Thus, my recommendation is to leave it be, despite the fact that an hour stuck at 0% is excessive for a resize operation. If it's still at 0% after, say, five or ten hours, then chances are it's hung and you might as well reboot.

If your Windows system still boots at this point, my recommendation is to resize the Windows partition using the tools built into Windows. These stand a better chance of working than do the Ubuntu tools. You can then pick the "advanced" or "manual" setup option in the Ubuntu installer (I don't remember which term is used) and set up your Ubuntu partitions in the free space. I recommend creating a root (/) partition of 5-20GB, a swap partition of 1-2 times your RAM size, and a /home partition that fills the rest of what you want to devote to Ubuntu. Make them all logical partitions.

---

### Post by jlaki on 2010-05-20
> **Tweep Cat said:**
> my **Delete** Inspiron

Delete Inspiron, hahaha, sorry, I couldn't help it, I just hate Dell so much that I find this amusing. :D

---

