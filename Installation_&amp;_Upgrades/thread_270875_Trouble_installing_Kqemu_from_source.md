---
title: "Trouble installing Kqemu from source"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Gotterdammerung on 2006-10-03
Hi there, 

I've read [this]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") how to about installing qemu, and since I`ve installed qemu from aptitude, I've decided to complete the installation by source.

So, trying to install Kqemu compiling from source I'm getting the following error message:

```
user@desktop:/tmp/kqemu-1.3.0pre9$ ./configure --kernel-path=/lib/modules/2.6.15-27-k7/build
big/little test failed
Source path       /tmp/kqemu-1.3.0pre9
C compiler        gcc
Host C compiler   gcc
make              make
host CPU          i386

kernel sources    /lib/modules/2.6.15-27-k7/build
kbuild type       2.6
```

Does anybody know how to fix this?

Here is some info:

```
Linux desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

desktop:/tmp/kqemu-1.3.0pre9$ gcc -v
Destino: i486-linux-gnu
Configurado com: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

```

---

