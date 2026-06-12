---
title: "Problem with AVM-Driver"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Matl on 2006-12-14
Hello,

I have a problem with my AVM Fritz!USB v2.0-Card. I cannot make the sources from the avm-website.

One error I could get rid of with a tip in another forum, but now there is
root@stefanie:/usr/src/fritz# make
make -C src
make[1]: Betrete Verzeichnis '/usr/src/fritz/src'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/fritz/src modules
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /usr/src/fritz/src/main.o
/usr/src/fritz/src/main.c:85: error: unknown field ‘owner’ specified in initializer
/usr/src/fritz/src/main.c:85: warning: initialization from incompatible pointer type
make[3]: *** [/usr/src/fritz/src/main.o] Fehler 1
make[2]: *** [_module_/usr/src/fritz/src] Fehler 2
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [fxusb.o] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/fritz/src'
make: *** [src/fxusb.ko] Fehler 2

Any hints? The fxusb2-driver is not in the ubuntu-modules yet.

Thanks,

Martin

---

