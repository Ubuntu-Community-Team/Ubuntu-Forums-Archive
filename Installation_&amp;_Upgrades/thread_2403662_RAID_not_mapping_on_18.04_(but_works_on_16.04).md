---
title: "RAID not mapping on 18.04 (but works on 16.04)"
date: 2018-10-14
forum: Installation &amp; Upgrades
---

### Post by arrviasto on 2018-10-14
Hi,
I'm configuring new installation of Ubuntu 18.04 over 16.04 after upgrade tool told me it's not possible to upgrade. Almost everything works fine except main storage RAID 1.

Both system are functional (I can easily boot one or another), so I can compare those and move configurations if needed.

RAID in question is "hardware" or "bios" raid running on Marvell 88se9172 controller. It is visible on win7 as a single drive and in original linux as both 2 separate drives (sdd, sde) and "mapped" drive (dm-0). I remember having problems getting it running on the original system, but I don't remember the solution (it was a couple years ago).

On new system there are only 2 drives visible, but neither dmraid nor dmsetup yield no results (on original they output those mappings).

Apart from trying dmraid and dmsetup I compared dmesg from both systems, but didn't find any significant differences.

I've spent a couple of hours now trying to find a solution, but nothing seems to work.

---

