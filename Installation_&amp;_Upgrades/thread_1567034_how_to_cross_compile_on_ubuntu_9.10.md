---
title: "how to cross compile on ubuntu 9.10"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Khan_77 on 2010-09-03
i want to cross compile a software for a i686 linux distro 
i am using ubuntu 9.10 (i386) following is the error output i am getting when i am trying to cross compile that software

sudo ./configure --build=-i686-linux --host=i386-linux --enable-readline --prefix=/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for i386-linux-strip... no
checking for strip... strip
configure: WARNING: using cross tools not prefixed with host triplet
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking if malloc debugging is wanted... no
checking build system type... configure: error: /bin/bash ./config.sub -i686-linux failed
configure: WARNING: cache variable ac_cv_build contains a newline


Pls help

---

