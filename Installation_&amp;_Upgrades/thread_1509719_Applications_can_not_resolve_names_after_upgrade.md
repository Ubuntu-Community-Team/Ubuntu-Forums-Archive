---
title: "Applications can not resolve names after upgrade"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by ldarby on 2010-06-14
Upgrade 904 to 910 appeared to go OK but after restart, left system with a number of packages marked as requiring re-install. Apt-get update failed and many other problems. I discovered nslookup worked fine but apt, browser, etc could not resolve names.  Apt worked after adding ubuntu package sites to hosts file.  No packages report as broken. Network manager is disabled on this system (could not handle complex bridging).
~$ nslookup [www.ubuntu.com](www.ubuntu.com)
Name:	[www.ubuntu.com](www.ubuntu.com)
Address: 91.189.90.41

~$ wget [www.ubuntu.com](www.ubuntu.com)
--2010-06-14 16:11:30--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Resolving [www.ubuntu.com](www.ubuntu.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.ubuntu.com](www.ubuntu.com)'

---

