---
title: "LiveCD boot automounts a partition on /cdrom: is this a feature?"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by alexei.colin on 2012-07-19
Does anybody know how the block device to be mounted on /cdrom gets chosen when booting from LiveCD? Usually, it's /dev/sr0 as expected, however, I noticed this surprizing behavior: if I happen to have a hard-drive partition whose only content is exactly a copy of the CD content, then that partition gets mounted on /cdrom (the partition is used *instead of* the CD drive, and the CD drive device is never used at all).

Is this some sort of a clever feature? I couldn't find it being documented anywhere. Any details on this behavior? If it is a feature, then how does one turn it off? Thank you.

LiveCD: Ubuntu 12.04 i386 Desktop

---

