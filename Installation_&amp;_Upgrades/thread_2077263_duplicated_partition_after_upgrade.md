---
title: "duplicated partition after upgrade"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by owise1 on 2012-10-28
Hi Guys,

I appear to have a duplicated partition after an upgrade from 10.10 to 12.04 see attached.  One is /dev/sda2 and the other is /dev/sda5 (swap).  This is slowing down boot time as a disk check occurs every boot.  Can I delete one of the partitions../dev/sda2 as it appears to be the rogue.

cheers

Dave

---

### Post by darkod on 2012-10-28
This is normal, linux usually installs with two main partitions, the main root partition and the swap partition that servers like the swap file in windows, when the memory is full.

If it does disk or partition checks, something might be wrong with it.

---

