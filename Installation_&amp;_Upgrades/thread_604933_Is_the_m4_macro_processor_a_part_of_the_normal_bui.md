---
title: "Is the m4 macro processor a part of the normal build?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by furious70 on 2007-11-06
Never worked with this particular OS before, but I'm trying to set some internally written daemons up on another group's box that requires a suite of dvd burning tools, growisofs.  The makefile for that tool requires m4, which does not appear to be on this OS anywhere.  I've tried to build m4, but run into troubles there as well.  Does anyone have a binary for m4 that is compatible with this OS?  Or anyone run into this type of issue before?  The shell script, configure, that gave this log output is _way_ over my head.  It's too large to attach, but here's some of the log.

The build runs off the rails testing the gcc compiler:

```
configure:2572: checking for gcc
configure:2588: found /usr/bin/gcc
configure:2599: result: gcc
configure:2837: checking for C compiler version
configure:2844: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2847: $? = 0
configure:2854: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang 
--prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-ge
ttext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --pr
ogram-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enab
le-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2857: $? = 0
configure:2864: gcc -V >&5
gcc: '-V' option must have argument
```

---

