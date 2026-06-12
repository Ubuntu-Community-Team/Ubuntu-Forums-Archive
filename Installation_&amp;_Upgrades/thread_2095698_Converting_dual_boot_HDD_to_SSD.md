---
title: "Converting dual boot HDD to SSD"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by ubufan52 on 2012-12-17
I wanted to upgrade my Windows 7 / ubuntu 12.04 netbook with 256 GB HDD to a smaller 128 GB SSD drive without losing Windows. It took awhile to figure out, but looking back it was simple. Maybe this post will help somebody.

Overview: backup personal stuff from ubuntu, save windows, reinstall ubuntu.

The SSD drive from Crucial comes with USB adapter and clone software (EZ Gig IV). Although documentation not found by me, ez-gig does clone from larger to smaller drives. It copies all partitions, and allows some control over resizing of partitions onto the target SSD. After the clone Windows partitions were fine, but ext3 partition and grub2 were junk.

Boot-repair from sourceforge easily restored grub2 so that Windows could boot. Ubuntu installed nicely in the corrupted partition and reused the old swap partition.

Boot times seems up to 2x faster. For my 2gb RAM netbook and mix of applications one key tweak was to set swappiness=0.

---

