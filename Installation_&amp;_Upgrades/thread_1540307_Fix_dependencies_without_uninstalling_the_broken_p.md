---
title: "Fix dependencies without uninstalling the broken package"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by AshRice on 2010-07-27
I have some Adobe AIR stuff installed and previously I managed to find a file where I deleted the dependency requirements for the broken file. I forgot to keep a note of what that file was. Anyway I updated somethings and now it's bitching again. Know how to fix it now (install AdobeAir.bin instead of .deb) but it won't let me do ANYTHING because the dependencies are broken. 

What I would like to know(either one will do):
1. how to force apt-get and dpkg to shut up and do what I say while I fix it.
2. where to find the file where I can delete the dependency requirements for the AIR virtual packages.

...I find this dependency thing to be very atypical for Linux. Usually you can get do anything even if it will break your system completely. Why is the package management so anal retentive?

---

### Post by zvacet on 2010-07-28
```
sudo apt-get -f install
```

This will install dependencies.

---

