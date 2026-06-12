---
title: "Upgrade from 6.06 LTS to 6.10"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2008-05-19
Hi All

I try to update 6.06 to 6.10 by  gksu "update-manager -c" , 
try "Update" button, can not able to see 6.10 Update ?

moonhk@hex:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.2 LTS
Release:        6.06
Codename:       dapper
moonhk@hex:~$


moonhk@hex:~$ gksu "update-manager -c"

(gksu:6009): Gdk-WARNING **: locale not supported by Xlib

(gksu:6009): Gdk-WARNING **: cannot set locale modifiers
(update-manager:6010): Gdk-WARNING **: locale not supported by Xlib

(update-manager:6010): Gdk-WARNING **: cannot set locale modifiers
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(synaptic:6024): Gdk-WARNING **: locale not supported by Xlib

(synaptic:6024): Gdk-WARNING **: cannot set locale modifiers

(synaptic:6052): Gdk-WARNING **: locale not supported by Xlib

(synaptic:6052): Gdk-WARNING **: cannot set locale modifiers

(synaptic:6128): Gdk-WARNING **: locale not supported by Xlib

(synaptic:6128): Gdk-WARNING **: cannot set locale modifiers
moonhk@hex:~$

---

### Post by zvacet on 2008-05-19
Edgy is not supported anymore and that can be reason why you can not upgrade.Why don´t you upgrade directly from Dapper to Hardy?Instructions are [here.]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by moonhk on 2008-05-20
I try direct upgrade to 8.04. can not able to boot it.So, I try to Upgrade one by one.

---

### Post by kami_iwinaru on 2008-05-20
or you can just burn the cd or order them
upgrades to the new versions always seem to be buggy when you dowload them =|

---

