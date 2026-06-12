---
title: "Dapper to Edgy upgrade problem"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by Aggienator on 2007-01-25
I've tried doing the upgrade using gksu "update-manager -c". I click on the upgrade button for 6.10 and all seems to be going well untill I get an error box:

Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz) 404 Not Found

Any idea what I can do about this?

Help gratefully appreciated!

---

### Post by oldmanstan on 2007-01-25
did you change your sources.list file appropriately? because according to those urls it's still trying to get dapper packages
also, you should do```
sudo apt-get dist-upgrade
```
to upgrade your whole distribution

---

### Post by maxamillion on 2007-01-25
There is currently a known issue that has not been resolved with the update-manager. I recommend you either follow oldmanstan's advice or do the same using aptitude.

More on the update-manager bug: [https://launchpad.net/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/ubuntu/+source/update-manager/+bug/68027)

---

### Post by Aggienator on 2007-01-26
Thanks for this, sources.lst was the problem! Removed the lines for packages.freecontrib and all went smoothly! :)

---

