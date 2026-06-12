---
title: "Can't successfully upgrade Edgy &gt; Feisty Kubuntu"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by solidus126 on 2007-05-06
Hello, when I launch adept from KDE I can't successfully complete the upgrade to Kubuntu Feisty.  It gets hung up on the 95/99 file it needs before modifying the software channel and then reports this:

---

Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/edgy-plf/non-free/source/Sources.gz) 404 Not Found

---

I tried to report the bug, but Konqueror just crashes when I try to.  I want to upgrade to Kubuntu, not Gnome, and I haven't found someone with a similar post to this...

Thanks in advance!

---

### Post by zvacet on 2007-05-06
Coment that lines (put # sign infront of the line) and save sorce list
```
sudo aptitude update
```

---

### Post by solidus126 on 2007-05-06
As of now the problem seems to be solved, thank you very much!

:)

---

