---
title: "Mount parameters needed needed in fstab for bcache volume?"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2013-08-17
After upgrading to kernel 3.10.7, I've setup a volume with bcache using a 120GB Intel 330 series SSD to cache a 2GB HDD.

My question is, when setting up an SSD-only partition, I would add noatime and discard to the line in fstab that mounts the partition. Should I use the same parameters for mounting the bcache partition?

---

