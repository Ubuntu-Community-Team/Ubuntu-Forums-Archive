---
title: "Could not install 'nvidia-dkms-418-server'"
date: 2024-10-09
forum: Installation &amp; Upgrades
---

### Post by jt4u on 2024-10-09
I get this message during upgrade from 22.04 to 24.04.

_**Could not install 'nvidia-dkms-418-server'**_


**The upgrade will continue but the 'nvidia-dkms-418-server' package may not be in a working state. Please consider submitting a bug report about it**

installed nvidia-dkms-418-server package post-installation script subprocess returned error exit status 10

I don't know if this is the reason the upgrade was aborted.

_**Could not install the upgrades**_


The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

---

### Post by jt4u on 2024-10-09
Forget this. I restarted the upgrade a few times and it finally worked. No more additional drivers for NVDIA.

---

