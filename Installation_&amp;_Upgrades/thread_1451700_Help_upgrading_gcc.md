---
title: "Help upgrading gcc"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Puzky on 2010-04-10
Hi! I have problems with gcc and i think it is because of the version i have:


```
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-5ubuntu1)
```I don't know how to upgrade. Does somebody can help me?

---

### Post by RedSingularity on 2010-04-11
Post the output of 

gcc --version

For example here is mine.

```
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

---

### Post by Puzky on 2010-04-12
```
puzky@ubuntu:~$ gcc --version
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by RedSingularity on 2010-04-12
Yours is more up to date than mine it seems.  Did you try reinstalling gcc to see if that solves your problem?

---

### Post by partloer on 2010-04-13
I also have version 4.4.1 with just a desktop install of 9.10 with all updates.  You could check the update manager to make sure that you have the latest updates.

---

