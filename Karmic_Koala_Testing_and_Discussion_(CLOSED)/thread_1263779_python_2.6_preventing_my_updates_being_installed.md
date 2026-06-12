---
title: "python 2.6 preventing my updates being installed"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jwssr on 2009-09-11
For the past 2 days, synaptic and apt-get fail because of dependencies failure with python2.6...see dpkg --configure -a at bottom of post.

if I pull python2.6...I pull most of my apps...not an option...

any suggestions????

.......................................................................
dpkg --configure -a

Setting up python2.6-minimal (2.6.2-0ubuntu5) ...
update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python2.6:
 python2.6 depends on python2.6-minimal (= 2.6.2-0ubuntu5); however:
  Package python2.6-minimal is not configured yet.
dpkg: error processing python2.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.6:
 libpython2.6 depends on python2.6 (= 2.6.2-0ubuntu5); however:
  Package python2.6 is not configured yet.
dpkg: error processing libpython2.6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.6-minimal
 python2.6
 libpython2.6

---

### Post by seeker5528 on 2009-09-12
Looks like the file in this part of the error message is the problem:

> **jwssr said:**
> 
update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package

If I look at that file on my computer, it contains this text:```

wine
magic
0
MZ

/usr/bin/wine

wine


```

There is a new line at the end of the file, may or may not be necessary.

Later, Seeker

---

