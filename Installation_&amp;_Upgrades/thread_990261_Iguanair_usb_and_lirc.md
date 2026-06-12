---
title: "Iguanair usb and lirc"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by jfacemyer on 2008-11-22
I've tried recompiling lirc to include iguanair support.  I've got both the latest iguanair package installed (0.98.1-1) and have downloaded the source for lirc and tried compiling using the command ```
dpkg-buildpackage -us -uc
```
I just get the following error:

dh_shlibdeps -s
dpkg-shlibdeps: failure: no dependency information found for /usr/lib/libiguanaIR.so.0 (used by debian/lirc/usr/bin/irrecord).
dh_shlibdeps: command returned error code 512
make: *** [binary-arch] Error 1
dpkg-buildpackage: failure: fakeroot debian/rules binary gave error exit status 2


Anybody have any ideas how to fix this?  I can't even really figure out what's wrong (obviously there's no dep info, but what does that mean?)

---

### Post by SchneiderIS on 2009-01-08
I have the same problem.  Did you ever get a resolution to it?

---

