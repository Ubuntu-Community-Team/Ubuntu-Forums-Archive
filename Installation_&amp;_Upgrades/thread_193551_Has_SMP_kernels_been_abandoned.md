---
title: "Has SMP kernels been abandoned?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Juzz on 2006-06-10
I used to run the SMP kernels (after the tip in the breezy forums about choosing the right kernel - I have a PIV 2.8), but to my surprise the latest SMP kernel released had debug enabled and no newer kernel has been released since then.
Has the maintainers abandoned the SMP kernels? Are they so sure that noone has invested in dual-core CPUs that it doesn't matter?

---

### Post by angkor on 2006-06-10
SMP is included nowadays in the 686 and k7 kernels afaik.

```
 apt-cache search linux-image
linux-image-2.6.15-23-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-23-686 - Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV **SMP**/UP
linux-image-2.6.15-23-k7 - Linux kernel image for version 2.6.15 on AMD K7 **SMP**/UP
linux-image-2.6.15-23-server - Linux kernel image for version 2.6.15 on Server Equipment
linux-image-2.6.15-23-server-bigiron - Linux kernel image for version 2.6.15 on BigIron Server Equipment
linux-image-386 - Linux kernel image on 386.
linux-image-686 - Linux kernel image on PPro/Celeron/PII/PIII/PIV.
linux-image-k7 - Linux kernel image on AMD K7.
linux-image-server - Linux kernel image on Server Equipment.
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
```

---

