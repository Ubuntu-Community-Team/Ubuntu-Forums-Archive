---
title: "Karmic upgrade freeze"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by dylfreak6494 on 2009-11-24
During a ubuntu karmic install my pc froze and now won't boot. When I try to upgrade through aptitude it says"not using locking for read only lock file /var/lib/dpkg/lock

---

### Post by fancypiper on 2009-11-24
You may have to remove the package manager lock
sudo rm /var/lib/dpkg/lock

---

