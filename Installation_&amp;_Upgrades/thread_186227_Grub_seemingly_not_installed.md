---
title: "Grub seemingly not installed"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by sanderjd on 2006-06-01
I installed 6.06 on a SATA drive containing a pre-existing Windows XP installation. sda1 is formatted as ntfs and mounted at /media/sda1, sda2 is formatted as ext3 and mounted at / and sda3 is swap. After the installation seemingly completed successfully and I restarted, my computer booted directly into Windows, without Grub loading. This happened twice. What am I doing wrong?

---

### Post by pellgarlic on 2006-06-05
did you install grub into a partition, or into the mbr? whichever you did, you could try the other? not too familiar with the implications of using sata drives with grub...

---

