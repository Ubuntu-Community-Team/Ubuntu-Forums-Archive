---
title: "Unable to find Qt3 file /usr/lib/qt3/lib/libqt-mt.prl"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by rhb on 2007-09-22
I downloaded and tried to build a Qt3 source program, but make failed with the message:

make[3]: *** No rule to make target `/usr/lib/qt3/lib/libqt-mt.prl', needed by `Makefile'.  Stop.

Apparently the libqt3-mt package replaces the  original liibqt3 package, but it appears the files are not identical.  I was able to resolve another missing file by googling, and made a symbolic link on the name.  Does anyone know if there is a file I can link to to satisfy this one?

It appears difficult to develop with Qt3, because there are two somewhat incompatable versions of Qt3, and Qt4 seems to be completely incompatable with Qt3.  Maybe there's information somewhere about how to keep multiple versions of the Qt libraries on the system without conflict.

Thanks for your assistance.

---

### Post by ddrichardson on 2007-09-23
No idea - might have more success if raised in Programming?

---

