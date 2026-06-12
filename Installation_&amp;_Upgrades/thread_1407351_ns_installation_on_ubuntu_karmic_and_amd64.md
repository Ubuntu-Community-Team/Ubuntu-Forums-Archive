---
title: "ns installation on ubuntu karmic and amd64"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by ankscorek on 2010-02-15
hey guys

there are number of threads floating on installation of ns2..however i am unable to get it on my 64 bit system

ns: error while loading shared libraries: libotcl.so: cannot open shared object file: No such file or directory


can someone please help me with it

---

### Post by ankscorek on 2010-02-15
ok here is the solution

the installation is just

CC=gcc-4.3 ./install

use getlibs to resolve all dependencies

solved

---

