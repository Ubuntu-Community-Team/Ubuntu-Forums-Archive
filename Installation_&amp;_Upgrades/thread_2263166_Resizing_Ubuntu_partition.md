---
title: "Resizing Ubuntu partition"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2015-01-30
Hello,

My hard drive has WinXP (still needed for work on old projects) and Ubuntu. Ubuntu is on /dev/sda5 and is 19.06 GB (please see attached screenshots from GParted). There is unallocated space of 52.18 GB before the Ubuntu partition. I tried resizing the Ubuntu partition to take up the unallocated space but it doesn't work. **How can I get Ubuntu to absorb the unallocated space into its partition?**

The screenshots were taken from a LiveUSB distro with GParted.

Thanks very much!

---

### Post by clay7 on 2015-01-30
Solved: needed to enlarge sda2 (the extended partition) and then I could enlarge sda5.

---

