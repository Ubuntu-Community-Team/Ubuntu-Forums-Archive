---
title: "how to tell where the source came from inside a package?"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by graysky on 2012-01-15
I would like to know where the files within the ttf-droid package came from.  In other words, what is their upstream source?

[http://packages.ubuntu.com/oneiric/all/ttf-droid/filelist](http://packages.ubuntu.com/oneiric/all/ttf-droid/filelist)

---

### Post by Frogs Hair on 2012-01-15
My search cited this as the upstream url . [http://code.google.com/android/](http://code.google.com/android/)

---

### Post by graysky on 2012-01-15
> **Frogs Hair said:**
> My search cited this as the upstream url . [http://code.google.com/android/](http://code.google.com/android/)

THanks, but doesn't the packager document the location of source files on Ubuntu? Arch linux does this in the PKGBUILD.  For example:

```
pkgname=htop
pkgver=1.0
pkgrel=1
pkgdesc="Interactive process viewer"
arch=('i686' 'x86_64')
url="http://htop.sourceforge.net/"
license=('GPL')
depends=('ncurses')
makedepends=('python2')
optdepends=('lsof' 'strace')
options=('!emptydirs')
changelog=ChangeLog
source=(http://downloads.sourceforge.net/${pkgname}/${pkgname}-${pkgver}.tar.gz)
md5sums=('325112ca7947ea1f6d6441f631e00384')
```

You can clearly see where the upstream package came from...

---

### Post by dino99 on 2012-01-15
inside synaptic "get changelog" related to ttf-droid:


fonts-droid (20101110+git-2) unstable; urgency=low

  * Team upload
  * Rename source package to "fonts-droid" to fit the Font
    Packages Naming Policy.
  * Bump Standards to 3.9.2 (checked)
  * Avoid lintian warning about fonts being also in ttf-droid

 -- Christian Perrier <bubulle@debian.org>  Tue, 23 Aug 2011 06:10:13 +0200

Fonts-droid:
-- Christian Perrier <bubulle@debian.org>  Tue, 23 Aug 2011 06:10:13 +0200

---

