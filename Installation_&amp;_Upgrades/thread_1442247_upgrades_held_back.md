---
title: "upgrades held back"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by seattle vic on 2010-03-29
I'm running 10.04 and for several days now I get two packages that are grayed out and do not upgrade in upgrade-manager.  If I use the shell and apt-get I get the following message:

The following packages have been kept back:
  firefox-gnome-support update-manager

The system is functioning well, but these 2 packages just linger as I process probably hundreds of lucid upgraded packages.

---

### Post by zvacet on 2010-03-30
```
sudo apt-get dist-upgrade
```

---

