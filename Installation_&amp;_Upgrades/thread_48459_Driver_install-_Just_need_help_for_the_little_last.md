---
title: "Driver install- Just need help for the little last bit :)"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-07-12
Hi all,
Further to my kernel source saga, I've finally got SLMDM to compile properly.
However, there are still two problems-
1. I am told that **slamr.ko** is in an invalid module format, when attempting
```
modprobe slamr
``` after the install. Google tells me this is caused when attempting to use a module compiled with a different kernel source to the running (Obviously not true :D), and so I need to know how to disable this please.
2. The install creates /dev/slamr0, 1 and 2. However, these vanish on reboot which I believe to be related to the fact that the ko file is not working. I need to stop this.

Anyway, progress of a sort.

-Leezer-

---

