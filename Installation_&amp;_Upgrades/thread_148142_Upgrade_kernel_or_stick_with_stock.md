---
title: "Upgrade kernel or stick with stock?"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by epikos on 2006-03-21
So I'm wondering if its better to upgrade to the i686 kernel in synaptic or to stick with the stock i386. Is there any benefit to using i386? I've got an AMD Athlon XP (barton) 2800+, so my cpu is definitely i686 (or if I remember correctly there’s a amd kernel, too)

I'm just curious if you upgrade to one of your architecture or stick with stock? Do the packages you download change when you change kernel architecture? Or what all happens when you download the new synaptic package for i686?

Thanks,
Epikos

---

### Post by az on 2006-03-21
The k7 kernel is optimised for your cpu, not the 686 one.

You do not upgrade to a different architechture by installing a kernel configured for a k7 cpu, you are just changing the kernel.  The architechture is still 386.  There is no relevant performance gain in compiling all the 386 packages for 686.  There are only 386 packages in the repositories.  But you can still run a 686 (or k7) kernel in 386.

You will probably notice a small performance gain.  It is more noticeable on older hardware (500MHz cpu)

---

