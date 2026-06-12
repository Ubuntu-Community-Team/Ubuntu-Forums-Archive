---
title: "dual boot XP and 10.04 trouble"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by Don DeGregori on 2012-02-07
Shown on GParted:

/dev/sda1         NTFS   XP
/dev/sda2         extended
    /dev/sda5     ext3
unallocated
/dev/sda6         linux-swap

I removed a partition without thinking I would have boot problems
It was Ubuntu 10.10 on /dev/sda7 which probably had grub2 on it.

Would like get back to dual boot. Both sda1 and sda 5 should be OK and not corrupted. What should I do to get back up?

Don

---

### Post by zvacet on 2012-02-07
On sda7 install ubuntu and you should have dual boot again.

---

### Post by darkod on 2012-02-07
You fail to mention what is on sda5, another ubuntu installation?

If you removed ubuntu what do you expect to dual boot?

---

