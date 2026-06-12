---
title: "Upgrade from 10.10 to 11.04 fails"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by tr333 on 2011-05-02
I tried to upgrade Mythbuntu from 10.10 to 11.04 but it fails to download three packages, stopping the upgrade from finishing. The APT source is au.archive.ubuntu.com

```

Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/p/phonon-backend-xine/phonon-backend-xine_4.7.0really4.4.4-0ubuntu3_amd64.deb 403 Forbidden
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-100dpi/xfonts-100dpi_1.0.3_all.deb 404 Not Found
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/universe/x/xfonts-75dpi/xfonts-75dpi_1.0.3_all.deb 404 Not Found

```

I get the same results if i switch to archive.ubuntu.com

---

### Post by mörgæs on 2011-05-02
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/773660](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/773660)

---

### Post by tr333 on 2011-05-03
Thanks for the link.  I tried again with archive.ubuntu.com and still got 404 errors in the upgrade application.  Strange, because I could download the .deb packages from firefox on the same computer.  The upgrade appears to be working now after I downloaded the problem packages from firefox directly and installed with gdebi.

---

