---
title: "invoke-rc.d: unknown initscript, /etc/init.d/lxc not found"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by krupier on 2014-11-16
Hello,

I wanted to experiment with LXC and installed it (v.1.1.0~alpha2-0ubuntu3 ) on my Utopic. I got this very error: **invoke-rc.d: unknown initscript, /etc/init.d/lxc not found** and I wonder if I should file a bug report on Launchpad or there is something with my installation. I checked Launchpad and it seems such bug was already reported some time ago.

Later I went through the install scripts and I don't see how /etc/init.d/lxc is created - is there any helper used on the process? So I decided to check how it was before & downloaded the previous version of the package (1.0.6-0ubuntu0.1), checked the scripts and there also don't see how the startup file (/etc/init.d/lxc) gets created. That's why I write here instead of Launchpad. Any ideas?

---

### Post by krupier on 2014-11-17
It seems the problem was with packages database. I have removed all my mirror files (which is all info about Ubuntu paskages) from **/var/lib/apt/lists/** and after updating it, all was configured correctly. There's still no sign of **/etc/init.d/lxc** on the filesystem but no complains from invoke-rc.d. I wonder what can cause such data inconsistency. Can someone explain, please? Thank you.

---

