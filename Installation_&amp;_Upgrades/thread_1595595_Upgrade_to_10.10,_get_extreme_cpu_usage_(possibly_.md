---
title: "Upgrade to 10.10, get extreme cpu usage (possibly involving firefox)"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by timefly on 2010-10-13
It appears that something in Firefox triggers extremely high CPU usage  after upgrading from 10.04 to 10.10. [I]When booting the older 2.6.32  kernel, the problem goes away.
[/I]
**Symptoms**: Even with only a single  tab open (Google's mail service) my system begins to "stutter" after a  few minutes: The mouse cursor ceases to move smoothly and pulseaudio  reports dozens, even hundreds of events suppressed by ratelimit.c (audio  begins to skip worse and worse).

Yes, I've heard of complaints against Flash, and I'm not ruling it out,  but I'm unaware of Flash being active (or at least visible in the  current tab) when I have Firefox running. *In any case, the problem  manifests reliably with the 2.6.35 kernel **but not with 2.6.32**.*

**Setup**:  My system is an intel i7-920 (64bit, 4 hyperthreaded cores, reported as  8 cpus), nVidia G92 (9800GT) with proprietary drivers, 9GB RAM. It ran  10.04 beautifully. I'm using kubuntu, for what it's worth.

---

