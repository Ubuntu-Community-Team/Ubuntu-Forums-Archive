---
title: "reinstall OS LVM+Raid"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by diskmaster23 on 2010-01-30
I am looking to reinstall my Ubuntu OS, but I have a LVM+Raid array, but the OS is not installed on the LVM+Raid array. How do I bring the LVM+Raid array back up once I install the new os?

---

### Post by diskmaster23 on 2010-01-30
I came up with a solution of my own.

The answer:
[LIST=1]
[*]Install LVM and MDADM (if that is what you are using for your software raid)
[*]copy over your old LVM and part of the FSTAB for your mount points (hopefully you mount them by UUID)
[/LIST]

and that really should be it. The funny part is, my /dev/md0 is not mounted, but the raid is functioning fine. Hmm...I dunno, but it is working.

---

