---
title: "Compiling unsupported plugins"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Martje_001 on 2007-10-29
Hi,
I've done this:
```
git-clone git://anongit.compiz-fusion.org/fusion/plugins-unsupported
cd plugins-unsupported
```But when I run autogen:
```
martijn@gutsy:~/plugins-unsupported$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:21: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:145: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
configure.ac:21: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:145: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:9: installing `./missing'
configure.ac:9: installing `./install-sh'
metadata/Makefile.am:23: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL
metadata/Makefile.am:17: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:17: (probably a GNU make extension)
metadata/Makefile.am:20: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:21: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:21: (probably a GNU make extension)
src/3d/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/3d/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/3d/Makefile.am: installing `./depcomp'
src/atlantis/Makefile.am:30: `%'-style pattern rules are a GNU make extension
src/atlantis/Makefile.am:33: `%'-style pattern rules are a GNU make extension
src/fakeargb/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/fakeargb/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/mswitch/Makefile.am:22: `%'-style pattern rules are a GNU make extension
src/mswitch/Makefile.am:25: `%'-style pattern rules are a GNU make extension
src/snow/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/snow/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/tile/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/tile/Makefile.am:26: `%'-style pattern rules are a GNU make extension
autoreconf: automake failed with exit status: 1

```
:confused:

---

### Post by jsully1 on 2007-11-13
You'll need to install libgconf2-dev.

---

