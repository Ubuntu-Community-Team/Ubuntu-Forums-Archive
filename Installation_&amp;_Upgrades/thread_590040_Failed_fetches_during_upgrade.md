---
title: "Failed fetches during upgrade"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by m0ridin on 2007-10-24
Everything was going well until i got these errors:


Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

should i just remove the medibuntu.sos-sts.com entries from my sources file?

Thanks!

---

### Post by Seisen on 2007-10-24
Just add a "#" in front of both lines for medibuntu then update and upgrade.

---

### Post by m0ridin on 2007-10-24
> **Seisen said:**
> Just add a "#" in front of both lines for medibuntu then update and upgrade.

Thank you very much, this worked fine :)

---

