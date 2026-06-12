---
title: "How to use a package from cosmic in bionic?"
date: 2019-05-11
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2019-05-11
The package has a lower version in bionic than in cosmic, how do I use the newer version?

---

### Post by Frogs Hair on 2019-05-11
Is the newer package version superior or better and if so how ? I would leave the package as is unless you can't live with out it as you may end up with broken packages. If the package did install and work you would have to lock the version to keep it from downgrading. [Ubuntu Package Search]("https://packages.ubuntu.com/")

---

### Post by ping-wu on 2019-05-12
> **Frogs Hair said:**
> Is the newer package version superior or better and if so how ? I would leave the package as is unless you can't live with out it as you may end up with broken packages. If the package did install and work you would have to lock the version to keep it from downgrading. [Ubuntu Package Search]("https://packages.ubuntu.com/")

I guess the only to do this is to download the packages from disco repository (which happen to have the same version number as in cosmic) and apt install them in bionic?  If they don't work, then apt remove these packages and do reinstall from bionic repo.

---

### Post by CatKiller on 2019-05-12
> **ping-wu said:**
> The package has a lower version in bionic than in cosmic, how do I use the newer version?

Generally, you don't.

Each Ubuntu release has the version it has, and doesn't get newer versions.

You'll probably have more luck adding a PPA for newer versions than trying to install bare deb files. You might also find a snap, which is a self-contained way of running applications.

---

### Post by ping-wu on 2019-05-12
> **CatKiller said:**
> Generally, you don't.

Each Ubuntu release has the version it has, and doesn't get newer versions.

You'll probably have more luck adding a PPA for newer versions than trying to install bare deb files. You might also find a snap, which is a self-contained way of running applications.

Any tutorial that explains how one can go from the existing Ubuntu/Debian packaging to doing a snap?

---

### Post by CatKiller on 2019-05-12
> **ping-wu said:**
> Any tutorial that explains how one can go from the existing Ubuntu/Debian packaging to doing a snap?
There's [this one](https://itsfoss.com/use-snap-packages-ubuntu-16-04/). I've never used them, though.

---

### Post by Rubi1200 on 2019-05-12
There is also this tutorial:
[https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0](https://tutorials.ubuntu.com/tutorial/basic-snap-usage#0)

Have never installed snaps, only removed some and no adverse affects to the system (as far as I could tell).

---

