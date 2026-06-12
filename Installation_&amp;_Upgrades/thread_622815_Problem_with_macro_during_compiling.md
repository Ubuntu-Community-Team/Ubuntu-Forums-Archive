---
title: "Problem with macro during compiling"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by warnec on 2007-11-25
Hello. I wanted to compile Compiz Fusion after downloading it from git. I've had some errors. (don't remember what they were, but basically they said something not found) . Then i installed automake and autoconf.(automake 1.9, autoconf 2.61-4 and 2.31-58 ) and autoconf-archive. Then I've got these erros:
```

autoreconf2.50: running: /usr/bin/autoconf
configure.ac:23: error: possibly undefined macro: AC_PROG_INTLTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:39: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:196: error: possibly undefined macro: AM_GCONF_SOURCE_2
autoreconf2.50: /usr/bin/autoconf failed with exit status: 1

```

Then I've read somewgere to install libtool. then i got:
```

autoreconf2.50: running: libtoolize --copy
aclocal:configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
aclocal:configure.ac:196: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf2.50: running: /usr/bin/autoconf
configure.ac:23: error: possibly undefined macro: AC_PROG_INTLTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:39: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:196: error: possibly undefined macro: AM_GCONF_SOURCE_2
autoreconf2.50: /usr/bin/autoconf failed with exit status: 1

```

Any ideas what to do?

---

### Post by dips_xe on 2007-11-25
any particular reason you're compiling that in the first place?

---

### Post by warnec on 2007-11-25
well, I'm using script to download and compile CF, and it starts by downloading and compiling compiz.

---

### Post by kellemes on 2007-11-25
Have you seen this thread?
[http://forum.compiz-fusion.org/showthread.php?t=1986]("http://forum.compiz-fusion.org/showthread.php?t=1986")

---

### Post by warnec on 2007-11-25
I did, and proparbly makinng:
```

sudo apt-get build-dep compiz


```

Would help. However, I've specially made a no-xcb patch, because i don't want Compiz to use xcb as dependency, because then i can't use OP2M. I've inseretd the patch line and everything, and building depndencied automatically would surely make x11-xcb to install, which i don't want.

---

### Post by warnec on 2007-11-25
Ok, most of the problems were solved, now only remaining:
```

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.ac: 39: macro `AM_GLIB_GNU_GETTEXT' not found in library
aclocal: configure.ac: 196: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: aclocal failed with exit status: 1

```

Ok, after installing glib2-data, glib2-dev left:
```

maciek@maciek-ubuntu:~/pala/compiz$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.ac: 196: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: aclocal failed with exit status: 1

```

Getting closer to a success :D

libgconf2-dev made it. HURRAY! :D
```

maciek@maciek-ubuntu:~/pala/compiz$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is created
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
autoreconf: `aclocal.m4' is unchanged
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
[and so on..]

```

---

