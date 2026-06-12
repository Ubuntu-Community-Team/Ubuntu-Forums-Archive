---
title: "beryl: ./autogen.sh: 11: intltoolize: not found"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by ture_atlantis on 2006-12-22
im trying to install beryl from svn source, but getting compilation errors.  my questions are:
what does this error mean './autogen.sh: 11: intltoolize: not found'?
and what package defines the AM_PATH_GLIB macro?

the output from my compilation is

autoreconf2.50: Entering directory `.'
autoreconf2.50: configure.ac: not using Gettext
autoreconf2.50: running: aclocal 
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
autoreconf2.50: configure.ac: tracing
autoreconf2.50: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
autoreconf2.50: running: /usr/bin/autoconf
autoreconf2.50: running: /usr/bin/autoheader
autoreconf2.50: running: automake --add-missing --copy --no-force
autoreconf2.50: Leaving directory `.'
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

./autogen.sh: 11: intltoolize: not found
BUILD FAILED for beryl-core

---

