---
title: "make make: *** No targets specified and no makefile found.  Stop."
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by Kreg on 2006-10-10
Hey i am trying to install a program and have finally got through configure. I am now struggling with make. when i enter the command i get this response
make: *** No targets specified and no makefile found.  Stop.

how do i specifiy a target or get further along in the install process 

dir shows the following

ABOUT-NLS   config.guess  COPYING     INSTALL     macros         po
aclocal.m4  config.h.in   CREDITS     install-sh  MAINTAINERS    README
AUTHORS     config.log    data        intl        Makefile.am    src
autogen.sh  config.rpath  debian      libltdl     Makefile.in    TODO
BUGS        config.sub    depcomp     libtool     missing
ChangeLog   configure     doc         ltconfig    mkinstalldirs
compile     configure.ac  glame.spec  ltmain.sh   NEWS

i have done apt-get and have all the latest installers and make commands and such.

thanks for the help

kreg

---

### Post by jpkotta on 2006-10-10
configure should make a Makefile from Makefile.am and Makefile.in.  So, ```
./configure && make && fakeroot checkinstall
```

---

### Post by the_analyzer on 2007-10-16
hey, I have the same problem, im trying to install anjuta, and when i press make it says
that : Re: make make: *** No targets specified and no makefile found. Stop.

can anyone help me please?

---

