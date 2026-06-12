---
title: "CDemu?"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by rlmiii on 2007-02-21
i am attempting to install CDemu via this link.

[http://www.ubuntuforums.org/showthread.php?t=144236](http://www.ubuntuforums.org/showthread.php?t=144236)

automake1.6 would not install. this is what comes up.

```
rlmiii@rlmiii:~/cdemu-0.7$ sudo apt-get install build-essential checkinstall automake1.6 libtool gcc-3.4 bchunk nrg2iso
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
Package automake1.6 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.6 has no installation candidate
rlmiii@rlmiii:~/cdemu-0.7$
```

i changed it to 1.7 and it installed fine, although im not entirely sure that this newer version is compatible

this is what happens when i sudo make or make.

```
rlmiii@rlmiii:~/cdemu-0.7$ make
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/rlmiii/cdemu-0.7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
CC [M] /home/rlmiii/cdemu-0.7/cdemu.o
/home/rlmiii/cdemu-0.7/cdemu.c:642: error: unknown field ‘dev_ioctl’ specified in initializer
/home/rlmiii/cdemu-0.7/cdemu.c:642: warning: initialization makes integer from pointer without a cast
/home/rlmiii/cdemu-0.7/cdemu.c:646: error: ‘CDC_IOCTLS’ undeclared here (not in a function)
/home/rlmiii/cdemu-0.7/cdemu.c:1051: fatal error: opening dependency file /home/rlmiii/cdemu-0.7/.cdemu.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/rlmiii/cdemu-0.7/cdemu.o] Error 1
make[1]: *** [_module_/home/rlmiii/cdemu-0.7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [all] Error 2

```
am i doing something wrong?

---

### Post by yabbadabbadont on 2007-02-21
I don't know about your error, but you might try using the 0.8.0 version that was released on 2006-08-05.  Maybe there was a bug that they have fixed that is causing your problem?

[http://cdemu.org/](http://cdemu.org/)

---

### Post by rlmiii on 2007-02-21
Bingo. Problem solved, thank you!

---

