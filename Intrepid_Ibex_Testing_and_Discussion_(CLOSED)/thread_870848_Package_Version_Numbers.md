---
title: "Package Version Numbers"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Exsecrabilus on 2008-07-26
Can you guys list the new versions of apps/packages that are in 8.10 alpha 3? (Other than the ones mentioned in the Softpedia screenshot tour.)

The one I'm most curious about is Compiz. Did they upgrade to 0.7.6? What about PulseAudio? Does Intrepid have version 0.9.11?

Thanks.

---

### Post by Bachstelze on 2008-07-26
[http://packages.ubuntu.com](http://packages.ubuntu.com)

Search for your package name in distribution *intrepid*, and you'll get the version.

---

### Post by Exsecrabilus on 2008-07-26
Wow, all my years using Ubuntu, and I can't believe I forgot that. XD

---

### Post by taavikko on 2008-07-26
```
apt-cache show pkg
```
```
apt-cache policy pkg
```
Is also very handy

> apt-cache show compiz
Package: compiz
Priority: optional
Section: x11
Installed-Size: 68
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: all
Version: 1:0.7.7+git20080630-0ubuntu2
Depends: compiz-core (>= 1:0.7.7+git20080630), compiz-plugins, compiz-gnome, compiz-fusion-plugins-main (>= 0.7.7+git20080630), compiz-fusion-plugins-extra (>= 0.7.7+git20080630), libcompizconfig0 (>= 0.7.7+git20080630)
Filename: pool/main/c/compiz/compiz_0.7.7+git20080630-0ubuntu2_all.deb
Size: 34812
MD5sum: 0674580d1a0b02a132d3481e74e6d0a6
SHA1: 049d97c3e2ebd1281748c0e2deea403e96203080
SHA256: 17ece2bcc6809e80ca66699439acfde287b6a39c09da3cc2bfcde0fdb50da653
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users
 with special needs.
 .
 This meta-package provides the components necessary for running compiz. It
 provides the compiz core, a set of standard plugins, a window decorator using
 the Gtk toolkit and the files necessary to integrate compiz with the GNOME
 desktop environment.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop


---

### Post by Bachstelze on 2008-07-26
> **taavikko said:**
> ```
apt-cache show pkg
```
```
apt-cache policy pkg
```
Is also very handy

I believe this will only work if the user has the intrepid repositories enabled. Nothing indicates that this is the case, it seems to me that he just wants to see which version of Compiz is included in it, without actually installing it.

---

### Post by BackwardsDown on 2008-07-26
> **HymnToLife said:**
> I believe this will only work if the user has the intrepid repositories enabled. Nothing indicates that this is the case, it seems to me that he just wants to see which version of Compiz is included in it, without actually installing it.

But it is a way to compare the intrepid packages with the ones he has currently installed.

---

### Post by Exsecrabilus on 2008-07-27
[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is so laggy, using [http://archive.ubuntu.com/](http://archive.ubuntu.com/) instead.

---

### Post by ccw on 2008-07-27
> **Exsecrabilus said:**
> Can you guys list the new versions of apps/packages that are in 8.10 alpha 3? (Other than the ones mentioned in the Softpedia screenshot tour.)

The one I'm most curious about is Compiz. Did they upgrade to 0.7.6? What about PulseAudio? Does Intrepid have version 0.9.11?

Thanks.

[https://launchpad.net/ubuntu/intrepid](https://launchpad.net/ubuntu/intrepid)

---

