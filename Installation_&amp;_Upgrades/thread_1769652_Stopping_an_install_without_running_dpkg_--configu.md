---
title: "Stopping an install without running dpkg --configure -a"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by garikaib on 2011-05-28
Hi,

I started installing openbravo3 but the installation was taking forever so I interrupted it manually. However every time I try to run apt or any other package management software I am told to run dpkg --configure -a which basically tries to complete the Openbravo installation which cant seem to complete. May somebody please help me out of this loop.

---

### Post by zvacet on 2011-05-30
Try to remove package with 

```
sudo apt-get --purge remove <packagename>
```

---

