---
title: "python errors?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mgsfan on 2009-04-08
python update won't install for me and been getting this error..

(Reading database ... 211269 files and directories currently installed.)
Preparing to replace python2.6-minimal 2.6.1-1ubuntu11 (using .../python2.6-minimal_2.6.2~rc1-0ubuntu1_i386.deb) ...
Moving /usr/lib/python2.6/site-packages/farsight.so to new location:
  --> /usr/lib/python2.6/old-site-packages/farsight.so (already exist in /usr/local/lib/python2.6/dist-packages/
mv: cannot move `/usr/lib/python2.6/site-packages/farsight.so' to `/usr/lib/python2.6/old-site-packages/': Not a directory
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.2~rc1-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.2~rc1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


The following packages have unmet dependencies:
  python2.6: Depends: python2.6-minimal (= 2.6.2~rc1-0ubuntu1) but 2.6.1-1ubuntu

---

### Post by mgsfan on 2009-04-09
anyone know if a fix is out? still can't update.

---

