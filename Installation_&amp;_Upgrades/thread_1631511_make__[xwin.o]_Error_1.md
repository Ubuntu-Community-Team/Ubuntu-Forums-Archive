---
title: "make: *** [xwin.o] Error 1"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by ubichinon on 2010-11-26
Hi!

I tried to compile a program called molden on ubuntu 10.04 
and when I compile I get 

cc -c -DDOBACK -DHASTIMER    -c -o xwin.o xwin.c
xwin.c:3795: error: ‘linkat’ redeclared as different kind of symbol
/usr/include/unistd.h:812: note: previous declaration of ‘linkat’ was here
xwin.c: In function ‘DebugStructure’:
xwin.c:12857: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘struct QBOXSTRU *’
xwin.c: In function ‘write_spectrum’:
xwin.c:35000: warning: unknown conversion type character 0xa in format
make: *** [xwin.o] Error 1

Someone came across this or knows how to fix it?

Cheers

Ubichinon

---

### Post by rajc on 2010-11-30
```

sudo apt-get install gfortran libX11-6 libX11-dev libgl1-mesa-glx libgl1-mesa-dev build-essential mesa-common-dev libglu1-mesa-dev libxmu-dev wget xutils-dev

```

---

