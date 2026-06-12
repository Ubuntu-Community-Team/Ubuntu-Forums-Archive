---
title: "[SOLVED] Problems with dpkg-buildpackage, apt-get upgrade"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by geoog on 2007-12-01
Hello,

I building some packages using the following commands:
$apt-get build-dep PKG
$apt-get source PKG
$cd PKG_dir
$dpkg-buildpackage -b -uc
$cd ..
$dpkg -i PKS.deb

Until here everything is working perfect, the package installed works fine. The problem is the apt-get upgrade and the Update Manager. They always tell me that I have to upgrade the package that I just install to the new version, but the new version is exactly the version that I build and install.
By now I wouldn't like to force a chance in the version of PKG to avoid this error.
I'm using Gutsy with the all upgrades. I already test several packages, with all occurs what a describe above.
Someone can help me with that ? 

Thanks.

---

### Post by Pumalite on 2007-12-01
If you are happy with your working version, tick off the update.

---

### Post by geoog on 2007-12-01
Hello,

I found the solution for this problem, here:
[http://ubuntuforums.org/showthread.php?t=422931]("http://ubuntuforums.org/showthread.php?t=422931")

---

