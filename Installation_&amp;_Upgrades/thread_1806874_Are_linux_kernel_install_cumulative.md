---
title: "Are linux kernel install cumulative?"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by rocketnewton on 2011-07-18
I have the following kernels installs: 
2.6.32-32
2.6.32-31
2.6.32-30
2.6.32-29

I'm currently booting 29 and 32 and want to uninstall 30 and 31. Can I do that without affecting 29?

---

### Post by TBABill on 2011-07-18
You certainly can. They do not rely on each other, but I would caution you to always keep 2. One older one that you know works and a current one you use regularly. if you update and find the new one is great, then you can remove one of the older ones. That way if something installs and borks the kernel you can boot into the other.

---

### Post by drs305 on 2011-07-18
Here's a thread on removing older kernels. I highly recommend using Ubuntu Tweak.
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by rocketnewton on 2011-07-18
Thanks TBABill, that's exactly what I want to do!

---

