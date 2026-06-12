---
title: "2 drives become one RAID1 drive plus 2 normal ext4 drives"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by tom222 on 2016-01-05
The subject of this post should have had a question mark on the end...

I will be installing a new system tonight. Can anyone confirm that it is possible, and perhaps sensible, to do something like this with my two 1TB drives?

(we'll leave swap off for now)

sd**a**1 500 GB for raid mda1
sd**b**1 500 GB for raid mda1

so that's the root drive, the **mda1**


***then ***sda2 and sdb2 can be normal 500GB ext4 drives for storage.

Is this doable and not prone to issues?

THANKS!

---

### Post by tom222 on 2016-01-06
Disregard this thread. I went with one full drive of RAID1. I believe I *could *have left ext4 partitions at the end of my raid partitions...

---

