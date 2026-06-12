---
title: "How do I easily create a metapackage"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by darkshadow on 2006-06-06
I have recently been installing Linux on e few friends computers and would like to make managing them easy by creating a metapackage that just depends on every piece of software that I install on all the computers.
My aim is to make installation as easy as
1: live cd install
2: add all repositories
3: install my metapackage
4: let them run there system

then everytime I find a new piece of software I update my package and email it to everyone.

I have no experience with packaging so easy to follow instructions would be nice.

---

### Post by Jussi Kukkonen on 2006-06-06
The new maintainer's guide ([http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)) is probably overkill here, but take a look at [http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html](http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html)

Basically, all you need to do is write a control-file with dependencies and run dpkg-deb.

---

### Post by darkshadow on 2006-06-07
Thanks, that worked perfect. Now during my next clean install I just have to keep track of every package I install.

---

