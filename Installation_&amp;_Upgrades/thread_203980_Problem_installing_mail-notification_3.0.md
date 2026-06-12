---
title: "Problem installing mail-notification 3.0"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by djberndt on 2006-06-26
Hi, all.. I have a problem installing mail-notification 3.0:

When typing ./configure , it says that it's unable to fint the gnome libraries.

How do I find out where where the gnome libraries are located, and witch variable should be used after ./configure to point at the gnome libraries? :confused: 

```
checking for GNOME... configure: error: unable to find the GNOME libraries
```

```
root@sidekick:/home/tjolahoppsan/Desktop/mail-notification-3.0# ./configure --help
`configure' configures Mail Notification 3.0 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --datadir=DIR          read-only architecture-independent data [PREFIX/share]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --infodir=DIR          info documentation [PREFIX/info]
  --mandir=DIR           man documentation [PREFIX/man]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-mbox          disable mbox support
  --disable-mh            disable MH support
  --disable-maildir       disable Maildir support
  --disable-pop3          disable POP3 support
  --disable-imap          disable IMAP support
  --disable-ssl           disable SSL/TLS support
  --disable-sasl          disable SASL authentication support
  --disable-ipv6          disable IPv6 support
  --disable-gmail         disable Gmail support
  --disable-evolution     disable Evolution support
  --disable-sylpheed      disable Sylpheed support
  --enable-sylpheed-locking
                          enable .sylpheed_mark locking
  --enable-compile-warnings=no|yes|error
                          enable compiler warnings [no]
  --enable-debug          enable assertions and cast checks
  --enable-regression-tests
                          build and run regression tests
  --enable-maintainer-mode  enable make rules and dependencies not useful
                          (and sometimes confusing) to the casual installer
  --enable-shared[=PKGS]
                          build shared libraries [default=yes]
  --enable-static[=PKGS]
                          build static libraries [default=yes]
  --enable-fast-install[=PKGS]
                          optimize for fast installation [default=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --disable-libtool-lock  avoid locking (might break parallel builds)
  --disable-largefile     omit support for large files
  --disable-gtktest       do not try to compile and run a test GTK+ program
  --disable-schemas-install     Disable the schemas installation

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-gnu-ld           assume the C compiler uses GNU ld [default=no]
  --with-pic              try to use only PIC/non-PIC objects [default=use
                          both]
  --with-tags[=TAGS]
                          include additional configurations [automatic]
  --with-reentrant-resolver
                          specify that the system resolver is reentrant
                          [autodetect]
  --with-gconf-source=sourceaddress      Config database for installing schema files.
  --with-gconf-schema-file-dir=dir        Directory for installing schema files.  --with-evolution-source-dir=DIR
                          path to the Evolution source tree

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CXXCPP      C++ preprocessor
  F77         Fortran 77 compiler command
  FFLAGS      Fortran 77 compiler flags
  PKG_CONFIG  path to pkg-config utility
  GNOME_CFLAGS
              C compiler flags for GNOME, overriding pkg-config
  GNOME_LIBS  linker flags for GNOME, overriding pkg-config
  GMIME_CFLAGS
              C compiler flags for GMIME, overriding pkg-config
  GMIME_LIBS  linker flags for GMIME, overriding pkg-config
  EVOLUTION_PLUGIN_CFLAGS
              C compiler flags for EVOLUTION_PLUGIN, overriding pkg-config
  EVOLUTION_PLUGIN_LIBS
              linker flags for EVOLUTION_PLUGIN, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

Report bugs to <jylefort@brutele.be>.
```

---

### Post by jasutton on 2006-06-26
Try this:

```
sudo apt-get install libgnome-dev
```

---

### Post by djberndt on 2006-06-26
thank you for the help, but it didnt work. ./configure still says that it can't find the gnome libraries. ](*,) 
i guess they are allready installed, but i need the path :-?

---

### Post by jasutton on 2006-06-26
It may be looking for the gnome2 libs:

```
sudo apt-get install libgnome2-dev
```

*EDIT: I'm attempting to compile this app myself to see if I can pin down what dependency it needs, and the above suggestion didn't work...:(  I'll post back if I find it*

---

### Post by jasutton on 2006-06-26
I found what it needs:

```
sudo apt-get install gnome-core-devel
```

:)

---

### Post by djberndt on 2006-06-26
thank you so much for the help. I finaly got it to work!! [IMG]http://www.sporthoj.com/forum/images/smilies/nya/banana.gif[/IMG]

one last question; how did you find out about what library to download?

---

### Post by jasutton on 2006-06-27
Glad to help :)

I Googled for "unable to find the GNOME libraries" which lead me to [this item]("https://lists.ubuntu.com/archives/ubuntu-fr/2004-November/000780.html") on the ubuntu mailing list (in French, which I don't read, no less).

I couldn't read the majority of the message, but I could make out the package name that looked exactly like what I was looking for :)

---

