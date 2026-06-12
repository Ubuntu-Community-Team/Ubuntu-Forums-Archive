---
title: "hd-media installer fail to mount .iso file"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by WatsonJX on 2012-06-10
I was trying to use the hd-media installer to install 12.04 (i386) from the alternate .iso CD image. From the install log, it found the .iso file from my first partition. However it failed to mount it, the error is "loop" kernel module is not available. I looked at the /lib/modules/.../kernel/fs directory and loop.ko is not there.

Is this a known problem? Thanks.

---

