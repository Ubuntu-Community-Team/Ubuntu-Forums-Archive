---
title: "Not able to make libdvdcss2. Please help!!!"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by jaspreet on 2007-04-25
phoenix:~/dvd/libdvdcss-1.2.1$ make
Making all in src
make[1]: Entering directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
make  all-recursive
make[2]: Entering directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
Making all in dvdcss
make[3]: Entering directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src/dvdcss'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src/dvdcss'
make[3]: Entering directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DDVDCSS_DIST -g -O2 -c libdvdcss.c
rm -f .libs/libdvdcss.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DDVDCSS_DIST -g -O2 -c libdvdcss.c     -fPIC -DPIC -o .libs/libdvdcss.lo
libdvdcss.c: In function 'dvdcss_read':
libdvdcss.c:407: error: invalid lvalue in assignment
libdvdcss.c:417: error: invalid lvalue in assignment
libdvdcss.c: In function 'dvdcss_readv':
libdvdcss.c:461: error: invalid lvalue in increment
libdvdcss.c:469: error: invalid lvalue in assignment
libdvdcss.c:470: error: invalid lvalue in assignment
make[3]: *** [libdvdcss.lo] Error 1
make[3]: Leaving directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
make[1]: *** [all-recursive-am] Error 2
make[1]: Leaving directory `/home/jaspreet/dvd/libdvdcss-1.2.1/src'
make: *** [all-recursive] Error 1

---

### Post by tgm4883 on 2007-04-25
Is there a reason that you need to compile libdvdcss2 and not just use apt-get?

---

### Post by jaspreet on 2007-04-25
well, First I do not have a live internet connection to my laptop. Second, I would love to learn all this Linux stuff!! So if somebody could help me figure this out please!!!!!

---

### Post by tgm4883 on 2007-04-25
well the first is answered easily, download it on another computer and transfer it via (usb, cd, osmosis)

The second, i feel also as easy, this linux stuff, i never felt was about reinventing the wheel.  And while im not too sure about the options for libdvdcss2, i can't imagine that you would gain anything by compiling it yourself (experience aside)

---

### Post by jaspreet on 2007-04-25
> **tgm4883 said:**
> well the first is answered easily, download it on another computer and transfer it via (usb, cd, osmosis)

The second, i feel also as easy, this linux stuff, i never felt was about reinventing the wheel.  And while im not too sure about the options for libdvdcss2, i can't imagine that you would gain anything by compiling it yourself (experience aside)

Thanks for this convincing reply!! :lolflag: But I am not convinced yet. I really want to learn what makes a wheel go around, definately not reinvent it. So stil..... any help is appreciated!!!!!!

---

### Post by tgm4883 on 2007-04-25
> **jaspreet said:**
> Thanks for this convincing reply!! :lolflag: But I am not convinced yet. I really want to learn what makes a wheel go around, definately not reinvent it. So stil..... any help is appreciated!!!!!!

Whatever floats you boat man, but if your going to be compiling every single thing on your system then, well you have more free time than me

---

### Post by jaspreet on 2007-04-25
> **tgm4883 said:**
> Whatever floats you boat man, but if your going to be compiling every single thing on your system then, well you have more free time than me

Thanks for replying!! cause you are the only person who is replying atleast. It is not about free time. But I want to learn how to compile packages. I won`t compile every single thing. But a few so I may learn this thing.

---

### Post by seagull_065 on 2007-10-30
Jaspreet,

According to the error messages (in your original post) you are not doing anything wrong.  There appears to be a problem with the source that you're trying to compile.  

I would suggest first, trying to get a newer version of the source.  I believe the newest source is at version 1.2.9  Get that an try compiling it instead of the old version that won't compile.

---

