---
title: "Problem in compiling emelFM2"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by mirrro on 2005-09-29
Helo, I downloaded the latest tarball file of emelFM2 (a file commander)
[http://emelfm2.org/rel/emelfm2-0.1.2.tar.gz](http://emelfm2.org/rel/emelfm2-0.1.2.tar.gz)
I'm using Hoary
according to the web site I need:
Gtk+ >= 2.4
GCC >= 3.2
shell commands - file, find >= 4.2, grep, sed
I apt-got : libgtk2.0-0 , libgtk2.0-bin , libgtk2.0-dev , gcc-3.4 , and gcc-3.4-base
There is Makefile in the unpacked dir' so I used :   sudo make
but I got this error:
generating 'objs/src/utils/cell-renderers/mg-popup-entry.deps'
/bin/sh: cc: command not found
make: *** [objs/src/utils/cell-renderers/mg-popup-entry.deps] Error 127
what is error 127?  , and what's my problem here..
Thanks.

---

### Post by dsyates on 2005-11-26
I have built a deb package of the latest emelfm2 for ubuntu 5.10. It can be downloaded here:

[http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.1.3-1_i386.deb)

---

