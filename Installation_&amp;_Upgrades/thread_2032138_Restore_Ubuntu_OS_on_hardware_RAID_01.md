---
title: "Restore Ubuntu OS on hardware RAID 01"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by shayno90 on 2012-07-23
Basically, I built a dual booting system based on Asus RAID 1 hardware, OS of Windows 7 and Ubuntu 10.04.

Problem occurred when add Skype repository and package which corrupted update manager, sources.list and other related files.

Tried to remove the corrupted packages and restore sources.list but this did not work.

Tried to upgrade to ubuntu maverick meerkat 10.10, had a power cut during the upgrade and now Ubuntu does not boot nor does the recovery mode work.

So, now I would to know if it is possible to re-install Ubuntu with or without removing the hardware RAID and if I have to remove the RAID will this affect the working Windows 7 OS?

---

### Post by shayno90 on 2012-08-08
I was able to reinstall Ubuntu using the 64bit live cd as the 32bit live cd was unable to read the way the RAID1 mapped the partitions.

Make sure to use the correct live cd 32/64b bit depending on your machine architecture.

---

