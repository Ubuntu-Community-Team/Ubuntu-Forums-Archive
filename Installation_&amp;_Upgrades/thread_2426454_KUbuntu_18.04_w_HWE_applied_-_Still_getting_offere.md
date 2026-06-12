---
title: "KUbuntu 18.04 w/ HWE applied - Still getting offered 4.15x kernels.. WHY?"
date: 2019-09-09
forum: Installation &amp; Upgrades
---

### Post by LVDave on 2019-09-09
I'm running KUbuntu 18.04.3 and have applied the HWE updates that change from a 4.15.x kernel to 5.0.0x kernel. I've done the HWE "update" on a
16.04LTS system and after doing so, the old kernel versions were no longer offered. This doesn't happen for me on 18.04. When I run the KDE update
tool, and there's a new kernel offered, I have to manually uncheck the 4.15x items offered. What's going on??

Thanks

---

### Post by deadflowr on 2019-09-09
Remove linux-generic, and or linux-image-generic and linux-headers-generic.
linux-generic/linux-image-generic depend on the latest non-hwe kernel.
So it'll keep pulling in those non-hwe kernels.

---

### Post by LVDave on 2019-09-11
Thank you!! that fixed it!!!!

---

