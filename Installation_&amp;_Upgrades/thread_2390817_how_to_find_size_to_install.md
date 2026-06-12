---
title: "how to find size to install"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-02
before actually installing a package with apt-get install using just a package name (and perhaps the architecture and/or version, and before i even have the .deb file, i'd like to find out how much space the installation will use.  this needs to also account for keeping the .deb file in addition to all files, including configuration files that are going to be installed.  **how/where can i get this info?** if this is from an online list, it will need to have all versions to be sure i get the size for a specific version i might be choosing to install.

---

### Post by Xian on 2018-05-03
I won't swear on a stack of pancakes this meets all of your criteria ... but:

If you don't care about the dependency requirements:

```
apt-cache show <package> | grep Size
```

This will show both the package and installation size.

For example:

```
$ apt-cache show abiword | grep Size
Installed-Size: 4588
Size: 1253564
```

If you DO care about the dependency requirements:

```
aptitude install -sy <package>
```

For example:

```
$ aptitude install -sy abiword
The following NEW packages will be installed:
  abiword abiword-common{a} abiword-plugin-grammar{a} libabiword-3.0{a} libgoffice-0.10-10{a} libgoffice-0.10-10-common{a} liblink-grammar5{a} libloudmouth1-0{a} 
  libots0{a} libtidy5{a} libwv-1.2-4{a} link-grammar-dictionaries-en{a} minisat{a} 
0 packages upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,121 kB/8,039 kB of archives. After unpacking 39.8 MB will be used.
Would download/install/remove packages.
```

---

### Post by Skaperen on 2018-05-03
i think i do need to know the dependencies, but individually, so that a package that 20 others depend on is not counted 20 times ... but only once.  so i think i need to resolve all dependencies first, and make a combined list, and add up those, so each package to be installed is added once (not including dependencies in this total because dependent packages will be in this list).

---

