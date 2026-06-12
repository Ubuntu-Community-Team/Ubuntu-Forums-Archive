---
title: "Compiling Gnofract4d on Ubuntu Edgy"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by Botondus on 2007-06-20
Gnofract4d is a really nice fractal program for linux but i can't seem to get it installed on my Ubuntu Edgy machine.
At the moment there are no packages of this program in repositories to my knowledge so i would like to compile it.
I managed to get rid of most other warning by installing some needed -dev libs through synaptic but i can't seem to find where this "cc1plus" comes from 
 This is the output when i try to build it, i hope someone can help me with this:

```
boti@xorcer-ubuntu:~/Fraktals/gnofract4d-3.4$ ./setup.py build
NO JPEG HEADERS FOUND
running build
running build_py
running my_build_ext
compiling with None
building 'fract4d.fract4dc' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT=1 -DGCONF_ENABLED=1 -DPNG_ENABLED=1 -UNDEBUG -Ifract4d/c -I/usr/include/python2.4 -c fract4d/c/fract4dmodule.cpp -o build/temp.linux-i686-2.4/fract4d/c/fract4dmodule.o -O0 -Wall -I/usr/include/libpng12
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
error: command 'gcc' failed with exit status 1

```

---

### Post by Botondus on 2007-06-20
Nevermind, i found out what the problem is. I have only C compiler installed, i also need a C++ compiler.
Dunno why i didn't think of it before.:p

---

