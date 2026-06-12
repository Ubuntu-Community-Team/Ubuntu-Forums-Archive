---
title: "Completely removing VMware Server"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by akawale on 2007-10-05
I installed VMware server using a repositories. I uninstalled it because I wanted to upgrade to the latest version, which was not available in the repository yet.

Unfortunately, while uninstalling I didn't 'completely remove' (purge) it.
As a result I can't install VMware server again, neither by using apt-get nor by executing the install script provided with the binary distribution.

Can anyone suggest how I can 'completely remove' VMware, so I can install it again?
Thanks.

---

### Post by Pumalite on 2007-10-05
Try:

sudo apt-get remove --purge VMware

---

