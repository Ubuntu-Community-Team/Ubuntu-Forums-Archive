---
title: "Unable to upgrade to 16.04, segmentation fault"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by sezhiana on 2016-06-08
Hi,

I am trying to upgrade from 15.10 to 16.04. The software updater says that there is upgrade but exists without doing anything. Tried using the terminal (sudo update-manager -d), it again opens the software updater and when trying to upgrade the terminal displays "Checking for a new Ubuntu release
Segmentation fault" and exits from the updater.

Kindly help.

Thanks.

Selian

---

### Post by Impavidus on 2016-06-09
The way to upgrade from 15.10 to 16.04 using terminal is the command```
sudo do-release-upgrade
```The graphical way ought to work though. Something strange must be going on to get a segfault. Maybe first try and reinstall ubuntu-release-upgrader-core and update-manager? Or just do a clean install.

---

