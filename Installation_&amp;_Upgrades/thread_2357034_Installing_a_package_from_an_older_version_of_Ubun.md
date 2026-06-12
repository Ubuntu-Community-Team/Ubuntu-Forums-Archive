---
title: "Installing a package from an older version of Ubuntu to a newer version"
date: 2017-03-29
forum: Installation &amp; Upgrades
---

### Post by sbhattac on 2017-03-29
Hello,

I installed a software developed in a laboratory in Ubuntu 16.04.1. The software was developed for Ubuntu 14.04. When I try to run it, it gives the following error:
-
-

error while loading shared libraries: liblapack_atlas.so.3gf: cannot open shared object file: No such file or directory
-
-
I have searched alot and the package containing the library,  libatlas4gf-base does not exist in Ubuntu 16.04.1. Is it possible to  install a package from an older version of Ubuntu to a newer version?  Thanks in advance.

Sagnik B.






J'ai cherché et le paquet contenant la bibliothèque, libatlas3gf-base, n'existe pas sous Ubuntu 16.04.
Peut-on installer un paquet d'une ancienne version d'Ubuntu sur une version plus récente ?

---

### Post by Impavidus on 2017-03-29
Maybe the name of the package has changed. I can find libatlas3-base, libatlas-base-dev, libatlas-dev and some related packages. Maybe one of those will do.

Most libraries depend on other libraries and an old version of a library depends on old versions of other libraries, so if you try to install a package for an older version of Ubuntu on a newer version, you enter something known as dependency hell.

---

### Post by Keith_Helms on 2017-03-29
The more standalone the old package, the better.  I installed the 14.04 version of gnome-calculator on my 16.04 system by downloading the deb file from the 14.04 repository, deleting the 16.04 version, installing the 14.04 version, and then marking the package as locked.  I tried to do the same with gnome-mahjongg and the package depended on too many other packages to make it worth the trouble.

---

