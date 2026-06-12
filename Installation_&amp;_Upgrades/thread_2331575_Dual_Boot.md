---
title: "Dual Boot"
date: 2016-07-23
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-07-23
Currently I am dual booting Windows 10 1511 & Ubuntu 16.04.  My  question is will the anniversary update, on Aug. 2nd effect the grub  bootloader.

Henry

---

### Post by grahammechanical on 2016-07-23
Whose anniversary? Windows 10? I do not run Windows but from what I see posted on this forum I would say that any update to Windows 10 is likely to effect the loading of Ubuntu. If the update to Windows 10 re-writes the partition table than the re-write will ignore any Linux partitions. They will still physically exist but not listing them in the partition table will cause them to practically disappear.

Regards.

---

### Post by gordintoronto on 2016-07-23
It probably will not affect the grub loader, but it is always prudent to have a CD of Boot Repair.

---

