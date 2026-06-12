---
title: "Windows boot problem"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by vrenlos on 2008-07-21
Hello all,

I installed Hardy on partition 1 of my hdd (WinXP is on partition 0) however the first disk that I tried to install from had some damage and the first install did not complete.  I re-burned the disk from another pc and reinstalled Hardy again, and everything seemed peachy.

When I go to boot to WinXP, however, the grub loader allows me to select XP, then sits at its initial loading screen and never actually moves on to start booting windows.

Any ideas?  Are there any flags in a config file that may be set incorrectly or anything else I might want to look at?

Thanks for your time,
V

---

### Post by logos34 on 2008-07-22
Run error checking on windows partition--either start tapping F8 after you select windows entry to start in 'safe mode'>run>chkdsk /r, or else boot from xp cd>'r' for recovery console>chkdsk /r.

The boot flag should be set for windows partition

sudo fdisk -l

---

