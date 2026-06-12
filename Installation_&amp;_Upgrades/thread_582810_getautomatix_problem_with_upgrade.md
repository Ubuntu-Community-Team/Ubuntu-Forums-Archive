---
title: "getautomatix problem with upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jcorden on 2007-10-20
Just tried upgrading from feisty to gutsy and got the following error

Any ideas?

Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by Arenlor on 2007-10-20
Don't use getautomatix use the correct way, disable it and use the Ubuntu servers (do so in System > Administration > Software Sources) you can re-enable getautomatix after the upgrade.

---

### Post by forestpixie on 2007-10-20
and if you don't know how to do that - open the file to edit and pu # in front of lines which you want to ignore

```
gksudo gedit /etc/apt/sources.list
```

---

