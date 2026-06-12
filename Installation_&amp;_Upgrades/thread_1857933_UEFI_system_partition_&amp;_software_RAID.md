---
title: "UEFI system partition &amp; software RAID"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by oohshiny on 2011-10-11
Relevant hardware: 2x2TB HDDs partitioned using GPT, Intel Sandy Bridge motherboard with UEFI.

Is it possible to install the EFI system partition on a software RAID1 array? mdadm throws a warning when I attempt this (metadata at the start of the array) so I'm wondering if it's completely impossible, whether using 0.90 metadata (at the end of the array) would work, or if I need some sort of manual solution (cron job to mirror the EFI partition etc).

---

