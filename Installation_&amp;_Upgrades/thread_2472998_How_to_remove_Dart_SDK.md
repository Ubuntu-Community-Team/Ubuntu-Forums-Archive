---
title: "How to remove Dart SDK?"
date: 2022-03-20
forum: Installation &amp; Upgrades
---

### Post by esso10 on 2022-03-20
How to remove Dart SDK?

---

### Post by MAFoElffen on 2022-03-20
If you installed Dart SDK to Ubuntu suing packages, then look in your "Other Software Tab" in 'Updates &Software' application to look for which PPA you installed it from. A good guess would be from 
```

dartsim/ppa

```
The list out the packages to be removed via
```

sudo apt list libdart*

```
The character immediately following "libdart" is the version number that was installed at the time you installed it... Using those package names, you would uninstall them. For example for Current version 6:
```

sudo apt remove --purge libart6-dev libadart6-*

```
Then remove the ppa from your sources list.

If you installed from source, and/or installed other options, use the related DART installation webpage as reference and work backwards: [https://dartsim.github.io/install_dart_on_ubuntu.html](https://dartsim.github.io/install_dart_on_ubuntu.html)

---

