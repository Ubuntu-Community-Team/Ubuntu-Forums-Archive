---
title: "What problem with &quot;make&quot;"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by micericewice on 2012-08-30
I have to build exactly Apache-1.3.41 on Linux. I did succesfull before with this configure:

# ./configure --prefix=/usr --sbindir=/usr/sbin --libexecdir=/usr/lib/apache --sysconfdir=/etc/apache --includedir=/usr/include/apache --datadir=/var/www --localstatedir=/var/www --logfiledir=/var/log/apache --runtimedir=/var/run --enable-module=so --disable-module=auth_db --disable-module=auth_dbm

But, after I have some other installation test (php, httpd-2.x, etc), I try to reinstall apache-1.3.41, it got errors. With simple config:

# ./configure --prefix=$HOME/apache_1 --enable-module=so
-> it's succesful, then I run make cmd

# make
-> it's got errors:

===> src
make[1]: Entering directory `/home/trongvn/meisei/apache_1.3.41'
make[2]: Entering directory `/home/trongvn/meisei/apache_1.3.41/src'
===> src/regex
gcc -I.  -I../os/unix -I../include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DUSE_HSREGEX -DUSE_EXPAT -I../lib/expat-lite -DNO_DL_NEEDED `../apaci` -DPOSIX_MISTAKE   -c -o regcomp.o regcomp.c
gcc -I.  -I../os/unix -I../include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DUSE_HSREGEX -DUSE_EXPAT -I../lib/expat-lite -DNO_DL_NEEDED `../apaci` -DPOSIX_MISTAKE   -c -o regexec.o regexec.c
gcc -I.  -I../os/unix -I../include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DUSE_HSREGEX -DUSE_EXPAT -I../lib/expat-lite -DNO_DL_NEEDED `../apaci` -DPOSIX_MISTAKE   -c -o regerror.o regerror.c
gcc -I.  -I../os/unix -I../include   -DLINUX=22 -DHAVE_SET_DUMPABLE -DUSE_HSREGEX -DUSE_EXPAT -I../lib/expat-lite -DNO_DL_NEEDED `../apaci` -DPOSIX_MISTAKE   -c -o regfree.o regfree.c
rm -f libregex.a
ar cr libregex.a regcomp.o regexec.o regerror.o regfree.o
*** buffer overflow detected ***: ar terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x50)[0x33fdf0]
/lib/i386-linux-gnu/libc.so.6(+0xe4cca)[0x33ecca]
/lib/i386-linux-gnu/libc.so.6(+0xe43c8)[0x33e3c8]
/lib/i386-linux-gnu/libc.so.6(_IO_default_xsputn+0x95)[0x2c37e5]
/lib/i386-linux-gnu/libc.so.6(_IO_padn+0xc8)[0x2b7598]
/lib/i386-linux-gnu/libc.so.6(_IO_vfprintf+0x1cd5)[0x298e35]
/lib/i386-linux-gnu/libc.so.6(__vsprintf_chk+0xad)[0x33e47d]
/lib/i386-linux-gnu/libc.so.6(__sprintf_chk+0x2d)[0x33e3bd]
ar[0x804ec04]
ar[0x8050d38]
ar[0x80585c2]
ar[0x804b452]
ar[0x804c3fd]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x270e37]
ar[0x80494c1]
======= Memory map: ========
0023c000-00258000 r-xp 00000000 08:01 918324     /lib/i386-linux-gnu/ld-2.13.so
00258000-00259000 r--p 0001b000 08:01 918324     /lib/i386-linux-gnu/ld-2.13.so
00259000-0025a000 rw-p 0001c000 08:01 918324     /lib/i386-linux-gnu/ld-2.13.so
0025a000-003b4000 r-xp 00000000 08:01 918337     /lib/i386-linux-gnu/libc-2.13.so
003b4000-003b5000 ---p 0015a000 08:01 918337     /lib/i386-linux-gnu/libc-2.13.so
003b5000-003b7000 r--p 0015a000 08:01 918337     /lib/i386-linux-gnu/libc-2.13.so
003b7000-003b8000 rw-p 0015c000 08:01 918337     /lib/i386-linux-gnu/libc-2.13.so
003b8000-003bb000 rw-p 00000000 00:00 0 
005f8000-005f9000 r-xp 00000000 00:00 0          [vdso]
006ec000-00706000 r-xp 00000000 08:01 918365     /lib/i386-linux-gnu/libgcc_s.so.1
00706000-00707000 r--p 00019000 08:01 918365     /lib/i386-linux-gnu/libgcc_s.so.1
00707000-00708000 rw-p 0001a000 08:01 918365     /lib/i386-linux-gnu/libgcc_s.so.1
08048000-080b5000 r-xp 00000000 08:01 2290982    /usr/local/bin/ar
080b5000-080b6000 r--p 0006c000 08:01 2290982    /usr/local/bin/ar
080b6000-080b7000 rw-p 0006d000 08:01 2290982    /usr/local/bin/ar
080b7000-080bb000 rw-p 00000000 00:00 0 
09eb4000-09ef1000 rw-p 00000000 00:00 0          [heap]
b750f000-b770f000 r--p 00000000 08:01 1974014    /usr/lib/locale/locale-archive
b770f000-b7710000 rw-p 00000000 00:00 0 
b771e000-b771f000 rw-p 00000000 00:00 0 
b771f000-b7720000 r--p 002a1000 08:01 1974014    /usr/lib/locale/locale-archive
b7720000-b7722000 rw-p 00000000 00:00 0 
bfd7e000-bfd9f000 rw-p 00000000 00:00 0          [stack]
make[3]: *** [libregex.a] Aborted
make[3]: *** Deleting file `libregex.a'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/trongvn/meisei/apache_1.3.41/src'
make[1]: *** [build-std] Error 2
make[1]: Leaving directory `/home/trongvn/meisei/apache_1.3.41'
make: *** [build] Error 2

Please help me check it out! I'm newbie in Linux :(

---

### Post by vexorian on 2012-08-30
Do you really HAVE to build it? Are you sure that just getting the apache package from repositories won't be enough for you? (I mean, you are a newbie and I am not, and I never needed to do that).

right now it does not seem easy to debug what is going on, but I can say that this is the part where things fail:

```

ar cr libregex.a regcomp.o regexec.o regerror.o regfree.o
*** buffer overflow detected ***: ar terminated
```

It seems like a bad bug with the ar program. At this moment you don't have a lot of options, unfortunately. Unless you decide to try the repository (software center) instead.

Edit: Does the apache version you are attempting to install have specific gcc and libc requirements? Maybe they don't match.

---

### Post by micericewice on 2012-08-31
> **vexorian said:**
> Do you really HAVE to build it? Are you sure that just getting the apache package from repositories won't be enough for you? (I mean, you are a newbie and I am not, and I never needed to do that).

right now it does not seem easy to debug what is going on, but I can say that this is the part where things fail:

```

ar cr libregex.a regcomp.o regexec.o regerror.o regfree.o
*** buffer overflow detected ***: ar terminated
```

It seems like a bad bug with the ar program. At this moment you don't have a lot of options, unfortunately. Unless you decide to try the repository (software center) instead.

Edit: Does the apache version you are attempting to install have specific gcc and libc requirements? Maybe they don't match.
Yep! I think "ar" program got a bug because I got same problem when compiling Buildroot.
I have to install exactly apache-1.3.41 for the purpose building the same environment of the Embedded system on a kits
Do you have any suggestion for this case. I installed it successful before, but I don't know why it got stuck now

---

### Post by steeldriver on 2012-08-31
which version of binutils are you using? have you checked bug reports for binutils?

---

