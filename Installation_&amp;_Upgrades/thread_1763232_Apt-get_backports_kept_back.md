---
title: "Apt-get backports kept back"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Leslie Viljoen on 2011-05-20
Hi!

I am having some random 100% CPU problems while trying out KDE, so someone suggested I upgrade to 4.6.2, which is in the PPA here: [https://launchpad.net/~kubuntu-ppa/+archive/backports]("https://launchpad.net/%7Ekubuntu-ppa/+archive/backports")

Unfortunately, when I enable that PPA, only some of the packages upgrade, like kcalc, kamera, kmag, etc.

kdm and another 161 packages are 'kept back' and stay on 4.5.5. I am running Maverick (10.10), but this PPA seems to specifically be for Maverick. How can I upgrade KDE to 4.6.2?

---

### Post by zvacet on 2011-05-20
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

