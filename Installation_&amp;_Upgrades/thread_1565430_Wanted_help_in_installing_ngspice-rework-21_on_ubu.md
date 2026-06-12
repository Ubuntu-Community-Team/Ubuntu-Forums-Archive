---
title: "Wanted help in installing ngspice-rework-21 on ubuntu 9.04"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by RockerAsh on 2010-08-31
Hello.
I need help regarding the installation of ngspice on Ubuntu 9.04.
 
While searching for installation instructions on the internet I found many different options.
 
I chose the one which said that ngspice can easily be installed using the tarball named ng-spice-rework-21.tar.gz which I downloaded from sourceforge.net.
 
I extracted the files from tarball and found an INSTALL file which gave me the following order of cammands to use to install ngspice
 
 
*./autogen.sh*
*./configure*
*make*
*sudu make install*
 
 
when I first wrote *./autogen.sh *it gave me error that read 'install libtool first'
 
I downloaded an installed libtool successfully
 
When I again used *./autogen.sh *command it ran and gave an error as 'automake failed'
following is the excerpt from the actual error reported in terminal window
 
```

Running libtoolize
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize: `/usr/local/share/aclocal/libtool.m4'
libtoolize: `/usr/local/share/aclocal/ltoptions.m4'
libtoolize: `/usr/local/share/aclocal/ltversion.m4'
libtoolize: `/usr/local/share/aclocal/ltsugar.m4'
libtoolize: `/usr/local/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running aclocal 
Running autoheader
Running automake -Wall --copy --add-missing
src/Makefile.am:244: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:244: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:244: to `configure.in' and run `aclocal' and `autoconf' again.
src/Makefile.am:244: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/Makefile.am:244: its definition is in aclocal's search path.
src/ciderlib/input/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/ciderlib/input/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ciderlib/input/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
src/ciderlib/input/Makefile.am:3: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/ciderlib/input/Makefile.am:3: its definition is in aclocal's search path.
src/ciderlib/oned/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/ciderlib/oned/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ciderlib/oned/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
src/ciderlib/oned/Makefile.am:3: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/ciderlib/oned/Makefile.am:3: its definition is in aclocal's search path.
src/ciderlib/support/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/ciderlib/support/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ciderlib/support/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
src/ciderlib/support/Makefile.am:3: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/ciderlib/support/Makefile.am:3: its definition is in aclocal's search path.
src/ciderlib/twod/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/ciderlib/twod/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ciderlib/twod/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
src/ciderlib/twod/Makefile.am:3: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/ciderlib/twod/Makefile.am:3: its definition is in aclocal's search path.
src/misc/Makefile.am:4: Libtool library used but `LIBTOOL' is undefined
src/misc/Makefile.am:4: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/misc/Makefile.am:4: to `configure.in' and run `aclocal' and `autoconf' again.
src/misc/Makefile.am:4: If `AC_PROG_LIBTOOL' is in `configure.in', make sure
src/misc/Makefile.am:4: its definition is in aclocal's search path.
 
....
....
....
....
....
 
 
automake failed

``` 
 
Please Help me guys I need this software for my final year project, so you can understand the urgency of it.
 
Thanks in advance.

---

### Post by sdaau on 2011-05-03
Sorry to bump an old thread, maybe this wiki entry will help: 

[From_PSpice_to_ngspice-gEDA - Ubuntu Wiki](https://wiki.ubuntu.com/From_PSpice_to_ngspice-gEDA)

---

