---
title: "Problems adding multiverse repositories"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by core on 2005-11-06
Hi, I got breeze installed in portuguese (pt) language, but when folowing ubuntu guide for 5.10, i've found errors right on the start. when adding the universe and multiverse just like they said, an error box popped up sayin repositories indexes could not be downloaded:

[http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
[http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
(...)
[http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://pt.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 82.211.81.182 80]

is this really problems on the server-side? or am i doing anything wrong?

sorry bout my english. and about me being kinda noob on linux :) thanks.

---

### Post by Xian on 2005-11-06
Remove the instances of breezy-backports in your source list.
They are not yet active.

---

### Post by aysiu on 2005-11-06
[QUOTE=core]Hi, I got breeze installed in portuguese (pt) language, but when folowing ubuntu guide for 5.10, i've found errors right on the start.[/quote] There's a Ubuntu Guide for 5.10? That's news to me.

> when adding the universe and multiverse just like they said, an error box popped up sayin repositories indexes could not be downloaded Try using these repositories instead (see first link in my sig).

---

### Post by core on 2005-11-07
Thanks Xian, I think that was the problem, everything's fine now.

aysiu, I'm sure your repositories file is just fine but I think those are not the portuguese localized ones. and yes, there is a [guide]("http://help.ubuntu.com/starterguide/C/faqguide-all.html") for 5.10, but not an "unnoficcial starter guide". This one seems to be official, I got it from the wiki.

---

