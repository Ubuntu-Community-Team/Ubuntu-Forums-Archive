---
title: "Update Manager Error Hardy"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by mic1960 on 2008-05-26
Hi all,

since the update to Hardy running update-manager I got the following error:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/cache/apt/pkgcache.bin - open (13 Permission denied), E:The package lists or status file could not be parsed or opened.'

Also chowning to user.user or chmodding to 777 the files .bin in /var/cache/apt does not resolve the issue.

running apt from command line under root runs smoothly.

Any hints ?

Yours,

Mic

---

### Post by mic1960 on 2008-05-30
noone to have any suggestions ?

---

### Post by zvacet on 2008-05-30
I don´t know if this will work but will not do any harm

```
sudo aptitude update & sudo aptitude safe-upgrade
```

---

