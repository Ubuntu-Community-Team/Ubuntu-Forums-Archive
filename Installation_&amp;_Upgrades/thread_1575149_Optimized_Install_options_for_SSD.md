---
title: "Optimized Install options for SSD??"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by bluedalek on 2010-09-15
Hi All

Finally took the plunge and got myself an OCZ 32GB SSD for my main desktop.

I'm getting some mixed info on the 'best' (and I know thats a personal option in the end) configuration for partitions, ect..

Here are my specs:

AMD Phenom x4
4GB 800MHz Ram
nVidia geForce 9500w/512MB
OCZ 32GB SSD (sda)
WDC 200GB Sata HD (sdb)
Hitachi 500GB Sata HD (sdc)
LG Dual Layer Sata DVD Burner (sdd)

I'm already aware of the various optimizations for SSD drives, such as using noatime, a different IO scheduler and mounting my tmp & firefox cache in a ram disc.

What I am wondering, is what the best partition setup would be for what I have.  As an example:

sda - boot
sdb - home
sdc - storage

but as for the partitions such as /var and the others, I'm not sure what the best options would be to get the best bang for my buck.

Also, is a swap file required anymore, will I see an appreciable different in performance if I just did not use one?  If I need one, should it be on the SSD or one of the other drives?

any thoughts or suggestions will be greatly appreciated!

---

### Post by a_posse_ad_esse on 2010-09-19
I'm reading your question as one about performance.  I would say that you could certainly just put sda as /, sdb as /home, and sdc as storage (where you mount the second and third drives shouldn't affect performance).  The SSD will give you improved boot times, etc, though you may want to format this as ext2 to minimise the number of writes.

---

