---
title: "Apache2 reinstall"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by canucksailor on 2012-01-14
Ubuntu 11.04 -- I wanted to change my Apache2 from "worker" to "prefork".  

sudo apt-get remove apache2-mpm-worker apache2-threaded-dev 

worked fine, but I'm now going around in circles and would really appreciate some assistance:

sudo apt-get install apache2-mpm-prefork
The following packages have unmet dependencies: apache2-mpm-prefork :
Depends: apache2.2-common (= 2.2.16-6+squeeze4) but it is not going to be installed
Depends: apache2.2-bin (= 2.2.16-6+squeeze4) but 2.2.17-1ubuntu1.2 is to be installed

sudo apt-get install apache2.2-bin
apache2.2-bin is already the newest version.

sudo apt-get install apache2.2-common
The following packages have unmet dependencies: apache2.2-common :
Depends: apache2.2-bin (= 2.2.16-6+squeeze4) but 2.2.17-1ubuntu1.2 is to be installed

sudo apt-get install apache2.2-bin
apache2.2-bin is already the newest version.

Could someone please help with what package[s] I need???  I've tried looking for all packages that approach these names (e.g apache2.2.17-1ubuntu1.2) with no success.

And ... the first "apt-get remove" above is not reversible, an "apt-get install" produces the same dependency errors.

Many thanks,
Paul

---

