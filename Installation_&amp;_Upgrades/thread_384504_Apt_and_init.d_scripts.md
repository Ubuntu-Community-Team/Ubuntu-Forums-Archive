---
title: "Apt and init.d scripts"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by akibakei on 2007-03-14
Apt doesn't seem to remove /etc/init.d scripts and /etc/rc#.d symlinks when removing a package.
It also doesn't seem to install a fresh version of these when reinstalling a previously-removed package.

Is there a way to force apt to do this?

---

### Post by zvacet on 2007-03-14
```
sudo aptitude remove filename
```

---

