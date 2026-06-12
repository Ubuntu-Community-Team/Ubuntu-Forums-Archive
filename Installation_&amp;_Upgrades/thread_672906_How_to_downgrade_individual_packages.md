---
title: "How to downgrade individual packages"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by jarekl on 2008-01-20
Yesterday's upgrade of xserver-xorg-core broke something with the latest nvidia drivers and mythtv crashes every time I start it,  and I would like to revert that upgrade. 

I've found there is an option to dpkg, --force-downgrade, but I can't find the package that preceded the currently installed. 

Is there a general method of reverting the last upgrade of individual packages or a repository that keep a history of packages?

/jarek

---

### Post by rahimveron on 2008-01-20
You may do that through Synaptic, selec the package and do Package>Force Version from the Menu

---

### Post by ajgreeny on 2008-01-20
However, that assumes the previous package is still available, or still in your own /var/cache/apt/archives folder.  Many packages can not be downgraded this way.  As I have plenty of room I have set the option to keep all files in the cache, and not del;ete packages when no longer available.  I'm not certain if it would have helped in this case, but I think it should have, even if you had to use the terminal dpkg command.

---

