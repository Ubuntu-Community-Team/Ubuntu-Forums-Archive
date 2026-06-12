---
title: "Upgrade unavailable?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by cannoli on 2007-10-25
When I try to upgrade from 7.04 to 7.10 on my laptop the system can't seem to find the upgrade. I have verified my connection is working, as I'm typing this on the same system. The upgrade worked successfully on a vmware install. I've tried the "official" upgrade strategy with no luck.

Thanks!

---

### Post by Ziox on 2007-10-25
Try an manual upgrade:

sudo aptitude update && sudo aptitude dist-upgrade

---

