---
title: "Python-Setup tools... cannot install or remove anything anymore :("
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by WinterWeaver on 2007-09-20
HI,

I recently installed Boa, and it was nice. So I then wanted to see what PIDA has to offer, tried to install that from the repos, and then it killed my system...

basically, now, I cannot install any new aps. I cannot remove any apps. Here is the error I get whenever I try to install or remove ANYTHING

```
Selecting previously deselected package libwww-ssl0.
(Reading database ... 192250 files and directories currently installed.)
Unpacking libwww-ssl0 (from .../libwww-ssl0_5.4.0-11build2_i386.deb) ...
Selecting previously deselected package amaya.
Unpacking amaya (from .../amaya_9.53~dfsg.0-1_i386.deb) ...
Setting up python-setuptools (0.6c5-1ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libwww-ssl0 (5.4.0-11build2) ...

Setting up amaya (9.53~dfsg.0-1) ...

Errors were encountered while processing:
 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-setuptools (0.6c5-1ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
pycentral pkginstall: already exists: /usr/lib/python2.5/site-packages/setuptools.pth
dpkg: error processing python-setuptools (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-setuptools

```

can someone please assist?

ta,

WW

---

### Post by WinterWeaver on 2007-09-20
ok... I removed python-setuptools from synaptic... will see if it helps

EDIT:
ok.. after removing, and then re-installing. Everything seems to be working fine. wonder what will happen if I try install PIDA again?

---

### Post by WinterWeaver on 2007-09-20
WOOT ... it worked ... lol... what a funny problem...

:guitar:

---

