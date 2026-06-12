---
title: "Gutsy to Hardy issues, python-central"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by XetrovNocilis on 2008-07-13
I'm trying to upgrade Kubuntu from Gutsy to Hardy.  Previously I used the graphical Adept Manager to go from Feisty to Gutsy on this computer so I didn't think there would be any issue.

Everything ran fine until it hit python-central.  It blew up and then everything depending on python-central obviously had issues until the whole process hung.

The command line is telling me to run dpkg --configure -a, which the first thing it bombs out on is python-central.

```
dpkg --configure python-central
Setting up python-central (0.6.7ubuntu0.1) ...
pycentral: pycentral pkginstall: package envyng is not installed
pycentral pkginstall: package envyng is not installed
pycentral: pycentral pkginstall: package envyng is not installed
pycentral pkginstall: package envyng is not installed
pycentral: pycentral pkginstall: package envyng is not installed
pycentral pkginstall: package envyng is not installed
dpkg: error processing python-central (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-central

```

Everything else seems to be failing related to this issue.  It is not telling me that python-central is dependant on envy (which it shouldn't be) but I can't figure out what it is trying to tell me.  I've tried upgrading envy, removing envy, purging envy, nothing seems to work.

Any help would be greatly appreciated.

XN

---

### Post by Vadi on 2008-07-13
This is known, the package is broken... someone had a workaround here: [https://bugs.launchpad.net/ubuntu/+source/python-setuptools/+bug/236798](https://bugs.launchpad.net/ubuntu/+source/python-setuptools/+bug/236798)

Edit: actually it looks like a different one, but still related to python.

---

