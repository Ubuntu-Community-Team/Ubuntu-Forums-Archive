---
title: "upgrading from 6.10 to 7.04"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by talg on 2007-05-25
when trying to upgrade through the update manager, I keep getting the error message :
 
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz) 404 Not Found

any suggestions...?

---

### Post by EndPerform on 2007-05-25
It looks like PLF repositories are giving you the issue.  Try disabling any non-ubuntu repository (such as PLF or the like), then attempt your upgrade.  In my experiences, trying to upgrade from one release to another with third-party repositories can cause more issues than good.

As always, before trying an upgrade, make sure you have your important data backed up.  It's a rule of thumb I always follow.

---

