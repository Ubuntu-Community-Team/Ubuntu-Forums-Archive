---
title: "GParted won't start when booting ubuntu from USB"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by jakecoll on 2017-01-16
I have a dell xps 13 and the guides on installation I can find tell me to repartition space from gparted before installing (I've already attempted multiple installations!), but gparted won't start. Any help? If running sudo gparted it eventually says "Segmentation Failure (Core Dump)"

---

### Post by oldfred on 2017-01-16
Best to use Windows tools to shrink Windows and reboot immediately to allow it to run chkdsk which it needs after any resize.
Do you have Windows fast start up on, which is really just hibernation.
Linux NTFS driver will not mount (see) NTFS partitions that are hibernated or need chkdsk.

Is system UEFI? If so see link to many links & more info in my signature below.

---

