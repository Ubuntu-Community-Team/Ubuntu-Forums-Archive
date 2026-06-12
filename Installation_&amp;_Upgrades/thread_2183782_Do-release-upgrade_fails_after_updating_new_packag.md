---
title: "Do-release-upgrade fails after updating new package lists from mirror"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by mooninaut2 on 2013-10-26
It turns out that```
deb http://mirror.anl.gov/pub/ubuntu/ raring main
``` and ```
deb http://mirror.anl.gov/ubuntu/ raring main
``` are not the same when it comes to upgrades. The former works fine; the latter is treated as a third-party source and disabled, causing the upgrade to fail. So if you have mysterious issues updating package lists during an upgrade, make sure your mirror URL/URI matches the official mirror list exactly.

---

