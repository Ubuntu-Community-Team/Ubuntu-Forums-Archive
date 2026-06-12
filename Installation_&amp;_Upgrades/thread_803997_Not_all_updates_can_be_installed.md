---
title: "Not all updates can be installed"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by lsuengineer on 2008-05-22
Hi, I ran the updater after a couple of weeks of no internet to install several hundred updates. It gave me a message saying "not all updates can be installed, Run a partial upgrade to install as many updates as possible." Well, it let me install most of the updates before running the partial upgrade. However, I am subscribed to several launchpad PPA's and it will not let me install these five updates because they cannot be authenticated. It only gives me the option to close the window instead of continue without authentication. Is this an error in the PPA's or with my packages? I am running Hardy.

Thanks

---

### Post by Pumalite on 2008-05-22
sudo apt-get update
sudo apt-get upgrade

---

### Post by lsuengineer on 2008-05-22
After I do this it says:

The following packages have been kept back:
  f-spot ssl-cert wine xulrunner-1.9 xulrunner-1.9-gnome-support

The wine & xulrunner are from the PPA's

---

