---
title: "Help needed: compiling imlib2"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2006-09-26
Endeavour2 needs imlib2 to show images. (not installing Enlightenment - just endeavour) All goes well until the end of "make" when I get:

g -O2 -c rgbadraw.c
rm -f .libs/rgbadraw.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/X11R6/include -I../libltdl -I/usr/local/include -I/usr/local/include -I. -I.. -I../src -I../loaders -g -O2 -c rgbadraw.c  -fPIC -DPIC -o .libs/rgbadraw.lo
rgbadraw.c: In function '__imlib_draw_polygon_filled':
rgbadraw.c:2328: error: label at end of compound statement
rgbadraw.c:2334: error: label at end of compound statement
make[2]: *** [rgbadraw.lo] Error 1
make[2]: Leaving directory `/opt/imlib2-1.0.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/imlib2-1.0.6'
make: *** [all-recursive-am] Error 2


What do these recursive errors mean? What am I missing?

Thanks in advance.

---

### Post by Gotterdammerung on 2006-09-26
with CFLAGS are you using? and which imlib2 version? what it is your glibc and gcc versions?

---

### Post by Psquared on 2006-09-26
> **Gotterdammerung said:**
> with CFLAGS are you using? and which imlib2 version? what it is your glibc and gcc versions?


I'm not at my linux box, but as I remember the version of Imlib2 is the latest stable version from sourceforge.net. Not sure what you mean by Cflags. gcc is version 2.95. I have everthing related to compiling I could find installed from the Ubuntu repos. (make, automake, build-essentials, etc)

I am working on Dapper in Xubuntu. AMD XP (32 bit) processor with 512 mb of RAM and 165 gig harddrive. (plenty of room) Video card is just an average nVidia with latest drivers installed. I keep my kernel up-to-date.

---

### Post by Gotterdammerung on 2006-09-26
> **Psquared said:**
> I'm not at my linux box, but as I remember the version of Imlib2 is the latest stable version from sourceforge.net. Not sure what you mean by Cflags. gcc is version 2.95. I have everthing related to compiling I could find installed from the Ubuntu repos. (make, automake, build-essentials, etc)

I am working on Dapper in Xubuntu. AMD XP (32 bit) processor with 512 mb of RAM and 165 gig harddrive. (plenty of room) Video card is just an average nVidia with latest drivers installed. I keep my kernel up-to-date.

GCC 2.95 is a little old. Try updating to 3.4 at least.

---

### Post by Psquared on 2006-09-26
> **Gotterdammerung said:**
> GCC 2.95 is a little old. Try updating to 3.4 at least.

Actually, I think imlib2 is trying to use gcc 2.95. I have 3.4 installed --- but I will check when I get home. What are CFLAGS?

Also, what is the difference between libimlib2 (in synaptic as Deb) and imlib2? Are they not interchangeable? All I am trying to do is enable images for Endeavor2 file manager. I know that is part of the Enlightenment package, but I've already had my playtime with E17 and got tired of it very quickly. :-D

---

### Post by Gotterdammerung on 2006-09-27
> **Psquared said:**
> Actually, I think imlib2 is trying to use gcc 2.95. I have 3.4 installed --- but I will check when I get home. What are CFLAGS?

Also, what is the difference between libimlib2 (in synaptic as Deb) and imlib2? Are they not interchangeable? All I am trying to do is enable images for Endeavor2 file manager. I know that is part of the Enlightenment package, but I've already had my playtime with E17 and got tired of it very quickly. :-D

[CFLAGS]("http://gentoo-wiki.com/Cflags") are the default parameters you pass to gcc when compiling something.

Try runing gcc-config -l to check which gcc version your system is using.

I don't know if imlib2 and libimlib2 are the same thing. :???:

---

### Post by Psquared on 2006-09-28
> **Gotterdammerung said:**
> [CFLAGS]("http://gentoo-wiki.com/Cflags") are the default parameters you pass to gcc when compiling something.

Try runing gcc-config -l to check which gcc version your system is using.

I don't know if imlib2 and libimlib2 are the same thing. :???:

Thanks. Endeavour is a neat app, but I think it works better with Enlightenment, so I just deleted the whole thing. No longer need imlib2. BTW, I do have GCC 3.4 installed.

---

