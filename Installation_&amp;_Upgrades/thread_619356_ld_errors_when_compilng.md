---
title: "ld errors when compilng"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-11-21
I have been a long time Slackware user and I have compilrd many apps and I have never run into a problem like this.

I have just installed 7.1 and  did

apt-get install build-essentials

But now when I try to build a test.c app the ld says it can't find libraries that are in /usr/lib.

Example:
~/src/test$ cc -lpng12 test.c
/usr/bin/ld: cannot find -lpng12
collect2: ld returned 1 exit status

#ls -l /usr/lib/libpng*
lrwxrwxrwx 1 root root     18 2007-11-21 00:42 libpng12.so.0 -> libpng12.so.0.15.0
-rw-r--r-- 1 root root 139768 2007-10-24 20:53 libpng12.so.0.15.0
j
$ /sbin/ldconfig -p | grep libpng
        libpng12.so.0 (libc6) => /usr/lib/libpng12.so.0

So, libpng12 exists and is in the ld cache.

I tried several others libz libm. i.e. -lz -lm, the old standbys and they all yielded the same error.

So, why the hell is ls NOT finding these libraries??

999alfred

---

