---
title: "New kernel doesn't mount xfs"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by mark_g on 2007-04-27
Whenever I boot Ubuntu with the new 2.6.20 kernel, I get the message on bootup that /dev/hda2 (which is my xfs partition) doesn't exist and therefore /home is never mounted. My external FAT hd on the other hand is properly recognized and mounted.

Fortunately when I boot 2.6.17 everything still works perfectly. Reinstalling the kernel and hal didn't help and dmesg doesn't really give much information... 

Anyone else know/have this problem or is it a bug maybe?

---

