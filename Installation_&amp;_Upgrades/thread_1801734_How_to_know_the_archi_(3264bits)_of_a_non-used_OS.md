---
title: "How to know the archi (32/64bits) of a non-used OS ?"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2011-07-11
Hi
I am looking for a way to determine, from a live-CD, the architecture (32 or 64bits) of all Linux on the computer. (FYI for the developpment of next version of the Boot-Repair tool).

I tried with uname, even from chroot, but it seems to give only the archi of the live-CD OS.

Any idea ?  :D

---

### Post by macaholic on 2011-07-11
The first thing that comes to mind is looking for directories that would only be present on a 64-bit distribution, e.g. "/lib64". However, I'm not sure if that's universal to all Linux systems.

---

### Post by YannBuntu on 2011-07-11
That's a good idea, thank you.

**@all:** please could you check on the distros you know ?

---

