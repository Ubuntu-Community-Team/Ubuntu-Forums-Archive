---
title: "log4c and liblog4c"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by pars on 2006-02-22
aren't available..

(I've searched at [http://packages.ubuntu.com](http://packages.ubuntu.com))

I missed something? 

Thanks!
pars

ps: there are RPM packages but I dont want to use them in ubuntu.
I have found a tarball for log4c, but I only find an RPM for
liblog4c :-k

---

### Post by pars on 2006-02-23
I'm replying to my own question in case someone 
has the same pb:

I've found the RPM package on the web:
log4c-devel-1.0.12-1.i386.rpm

transformed it to DEB package using alien:
alien log4c-devel-1.0.12-1.i386.rpm

and installed it using dpkg: 
dpkg -i log4c_1.0.12-2_i386.deb

---

