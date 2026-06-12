---
title: "Trying to upgrade to breezy"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by jsmidt on 2005-11-17
I have hoary on my machine but when I change all my repo's from hoary to breezy, then hit```

apt-get dist-upgrade

```

I get:

```

ESTHER:/home/jsmidt# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
  abiword-common: Depends: abiword but it is not installable or
                           abiword-gnome but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by matthewv on 2005-11-17
try, before doing a dist-upgrade ```
sudo apt-get update
```This will update your package lists with the latest breezy packages

EDIT: You also have to run apt-get as superuser e.g sudo apt-get, not apt-get

---

### Post by mlomker on 2005-11-17
If the update doesn't work then try using one of the mirrors.  The main ones are sometimes out of synch.

---

