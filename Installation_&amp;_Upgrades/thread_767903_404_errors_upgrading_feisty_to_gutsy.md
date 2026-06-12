---
title: "404 errors upgrading feisty to gutsy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by evanct on 2008-04-26
i never bothered upgrading to gutsy. update manager won't let me upgrade directly to hardy, so im trying to upgrade to gutsy now, but i get this:

```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz 404 Not Found
```

how do i fix this? or is there a way to upgrade directly to hardy?

---

### Post by Partyboi2 on 2008-04-26
Open up software sources and disable all 3rd party repo's and try again.
You will need to upgrade to gusty before upgrading to hardy.

---

### Post by evanct on 2008-04-26
i did that but now when i just try to open update manager i get this:

```
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/cache/apt/srcpkgcache.bin - open (13 Permission denied), E:The package lists or status file could not be parsed or opened.'
```

---

### Post by evanct on 2008-04-26
nevermind i fixed that with sudo apt-get update

---

