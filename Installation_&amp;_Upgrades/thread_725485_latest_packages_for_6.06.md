---
title: "latest packages for 6.06?"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by YeppersDappers on 2008-03-15
I got the 6.06 (dapper) distro and am wondering, as a general linux and specificly debian newbie, if it is not possible to get the latest releases of the packages...
As i see there are unofficial repositories on the apt-get site ( [http://www.apt-get.org/main/](http://www.apt-get.org/main/) ) but isn't there a source, which gives me newer versions of all packages for my old dapper system??
For example i would like to have a later version of php. later than 5.1.2, which seems to be the standard in dapper. of course i would like to have 5.2.5 if possible ;) i know i can compile everything on my own, but am just wondering about this.

thanks in advance

---

### Post by mssever on 2008-03-15
Your best bet is to compile your own (possibly from debian unstable). pbuilder will help you there. The problem is that few people are using Dapper anymore, so there aren't likely to be too many updated packages for it. And aside from backports, Ubuntu policy prefers to remain with a particular version for the live of the Ubuntu release, only applying security fixes and some other bug fixes.

---

