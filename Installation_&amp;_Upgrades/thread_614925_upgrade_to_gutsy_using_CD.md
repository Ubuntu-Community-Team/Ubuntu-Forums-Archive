---
title: "upgrade to gutsy using CD?"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Titi on 2007-11-16
hello
i have a cd of ubuntu 7.10. i'd like to upgrade my system from 6.06 to 7.10, is this possible  without having to download all te updates, only using the CD?
thanks!

---

### Post by wolfen69 on 2007-11-16
a clean install is preferable to an upgrade. that said, i have never done it before, but i believe you can insert cd, then, in terminal:
```
update-manager
```
before all that though, go to system>administration>software sources and make sure to add cd to available sources.

a distribution upgrade should appear in update manager.

or, in terminal:
```
sudo apt-get dist-upgrade
```

---

