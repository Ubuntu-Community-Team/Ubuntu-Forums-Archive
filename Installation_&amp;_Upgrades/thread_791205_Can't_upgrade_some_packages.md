---
title: "Can't upgrade some packages"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by SuperBo on 2008-05-12
Why I can't upgrade some packages. The system inform that they have been kept back.
Please help me upgrade them.
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr libawn-bzr
  libqt4-core libqt4-gui linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

---

### Post by amohanty on 2008-05-12
You could try a dist upgrade:

sudo apt-get dist-upgrade

Typically you need to do this when upgrading between desitributions ie feisty and hardy or between the hardy alpha releases and the hardy final release.

HTH
AM

---

### Post by SuperBo on 2008-05-12
Thank you, now I can update those packages.

---

