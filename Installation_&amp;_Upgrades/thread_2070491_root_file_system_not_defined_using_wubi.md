---
title: "root file system not defined using wubi"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by cytricks on 2012-10-12
I Just got a new Vizio CN15-A2

It has a 1 TB HDD with a 32 gb SSD for caching.

When i was installing Ubuntu on it i was getting "root file system not defined".

I did some research and i was an idiot for not thinking about it.

THE FIX!!

Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

---

