---
title: "horizontal lines"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by waspinator on 2010-10-13
Hi,

Just installed 10.10 and my screen is all messed up (horizonal lines across screen, cut off on the right). It looked this way during installation too, but I thought an update might fix it but it didn't.

I have an intel gpu:
Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

I tried holding down shift during boot and adding "nomodeset" to the grub parameters but then it goes to console, and startx says there are no screens available. 

I tried to use the "Additional Drivers" tool but it didn't find any. Is there some other driver I can install? I think it uses the i915 kernel module.

I had the same problem in 10.04, but adding nomodeset to grub helped.

Thanks,
Waspinator

---

