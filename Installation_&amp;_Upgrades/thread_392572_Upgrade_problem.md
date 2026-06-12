---
title: "Upgrade problem"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by onurguzel on 2007-03-24
I have Ubuntu 6.06 installed on my computer with GNOME, KDE and XFCE desktop environments. I had KDE 3.5.2 and wanted to upgrade to 3.5.6... To upgrade other packages too, I replaced all "dapper"s into "edgy" in sources.list...
```
sudo apt-get update
sudo apt-get dist-upgrade
```After the download of packages (about 710MB) and install, I restarted my computer but couldn't be able to boot. None of my drivers is being read.

What do I gotta do?

---

### Post by onurguzel on 2007-03-25
The problem is about X. i810_drv.so module couldn't be loaded.

No idea?

---

