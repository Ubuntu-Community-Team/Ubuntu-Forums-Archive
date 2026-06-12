---
title: "Failure to upgrade realtime kernel"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by macabro22 on 2008-06-06
Hello,

Cansomeone help me with this??

```
E: linux-image-2.6.24-17-generic: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.24-18-generic: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.24-17-rt: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.24-18-rt: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-18-rt: dependency problems - leaving unconfigured
E: linux-backports-modules-hardy-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-18-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-18-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-rt: dependency problems - leaving unconfigured
E: linux-rt: dependency problems - leaving unconfigured

```

---

### Post by Pumalite on 2008-06-06
sudo dpkg --configure -a
Post the output.

---

