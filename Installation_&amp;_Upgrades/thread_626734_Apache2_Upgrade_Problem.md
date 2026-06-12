---
title: "Apache2 Upgrade Problem"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by wruwtrix on 2007-11-29
Any insights into the following error while trying to install apache2?

phidev:/home/abc5# apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apache2: Depends: apache2-mpm-worker (>= 2.2.6-1) but it is not
going to be installed or
                   apache2-mpm-prefork (>= 2.2.6-1) but it is not
going to be installed or
                   apache2-mpm-event (>= 2.2.6-1) but it is not going
to be installed
 locales: Depends: glibc-2.6-1
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or
specify a solution).

Thanks for your help!

---

