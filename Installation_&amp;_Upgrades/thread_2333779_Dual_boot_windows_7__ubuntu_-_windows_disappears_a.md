---
title: "Dual boot windows 7 / ubuntu - windows disappears after encryption"
date: 2016-08-13
forum: Installation &amp; Upgrades
---

### Post by menshevik on 2016-08-13
Hello
I had a perfectly fine dual boot laptop running WIndows 7 and Ubuntu, until my company insisted I encrypt the Windows partition (McAfee), after which Windows no longer shows up in the boot loader.  Can this be repaired or am I out of luck?

thanks much

---

### Post by oldfred on 2016-08-13
The few that have posted with encrypted Windows had proprietary boot code in MBR.
Those that installed grub could not boot Windows from grub. And usually were able to use the proprietary software's repair tools to reinstall a MBR.

And those that could dual boot then installed grub to sdb and booted from sdb. Where sdb is any other drive, flash drive or even writeable DVD. If flash drive you only need MBR and can still use it for data.

---

