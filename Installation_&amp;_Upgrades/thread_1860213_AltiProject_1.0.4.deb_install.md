---
title: "AltiProject 1.0.4.deb install"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by jefftb on 2011-10-14
Trying to install software AltiProject.  First attempt threw me a wrong architecture.

So I tried a force command...here's what I got back.

sudo dpkg --force-architecture -i altiproject_1.0.4.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 258757 files and directories currently installed.)
Preparing to replace altiproject:i386 1.0.4-1 (using altiproject_1.0.4.deb) ...
Unpacking replacement altiproject:i386 ...
dpkg: dependency problems prevent configuration of altiproject:i386:
 altiproject:i386 depends on bash (>= 3.0).
dpkg: error processing altiproject:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 altiproject:i386

Ideas?

---

