---
title: "msyqlcc install HH libqt-mt.so.3 error"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by keabuntu on 2008-11-19
Installed mysqlcc, when running "mysqlcc" from terminal, getting:

mysqlcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

from my google-fu i think i need to rebuild library?  anyone know what the issue / how to correct here?

---

### Post by keabuntu on 2008-11-20
In case anyone else has this difficulty:

apt-get install libqt3-mt-mysql

Installs the correct package found here:  

[http://packages.ubuntu.com/hardy/libs/libqt3-mt-mysql](http://packages.ubuntu.com/hardy/libs/libqt3-mt-mysql)

---

