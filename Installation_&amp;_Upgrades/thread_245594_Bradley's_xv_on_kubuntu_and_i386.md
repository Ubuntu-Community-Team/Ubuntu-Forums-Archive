---
title: "Bradley's xv on kubuntu and i386"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by JarkkoN on 2006-08-28
I would like to install John Bradley's "xv" on a i386 and kubuntu. 
However, unpacking a debian package (.deb) fails: 
---
Unpacking xv (from xv_3.10a-26_i386.deb) ...
dpkg: dependency problems prevent configuration of xv:
 xv depends on libpng2 (>= 1.0.10); however:
  Package libpng2 is not installed.
...
dpkg: error processing xv (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing xv
# apt-get install libpng2
Reading package lists... Done
Building dependency tree... Done
Package libpng2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libpng2 has no installation candidate 
---
Building a new debian package from source didn't work well either, I just couldn't get it working on a i386. 

Has anybody worked this out before? Any suggestions? I would appreciate any help.

---

### Post by Rog131 on 2006-08-28
> xv depends on libpng2 (>= 1.0.10); however:
Package libpng2 is not installed.

Install libpng2 ?


libpng2:
> is only available from another source

Find another source ?

---

### Post by JarkkoN on 2006-08-28
Thanks for your help. 

Would someone like to propose another source? 

A debian user claimed that the name for libpng2 was different in debian and in ubuntu. The same content is there in kubuntu, but it can't be found when unpacking the xv debian package. I wonder if this could really be true. 

The packages libtiff3g and xlib6g were also missing in xv installation, in addition to the libpng2 that was used as an example. 

Thanks anyway, 
Jarkko

---

