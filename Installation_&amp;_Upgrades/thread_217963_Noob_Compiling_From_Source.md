---
title: "Noob Compiling From Source"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by gabrieliscool on 2006-07-17
I Cant Seem To Compile Music Applet, Can Somebody Help Me?

> gabriel@Home:~$ cd /home/gabriel/Desktop/music-applet-0.9.2
gabriel@Home:~/Desktop/music-applet-0.9.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for glib-genmarshal... no
configure: error: glib-genmarshal executable not found in your path - should be installed with GLib
gabriel@Home:~/Desktop/music-applet-0.9.2$



---

### Post by croak77 on 2006-07-18
> **gabrieliscool said:**
> I Cant Seem To Compile Music Applet, Can Somebody Help Me?

You need libglib2.0-dev.

---

### Post by gabrieliscool on 2006-07-18
Thank You!

---

