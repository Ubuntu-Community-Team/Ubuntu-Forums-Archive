---
title: "Fuppes will not make install"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by timstone on 2008-10-05
after configuring and running the make command i ran sudo make install and it ran for a bit, then it stops and this is what shows at the end...

```

Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'fuppes' '/usr/local/bin/fuppes'
/usr/bin/install -c .libs/fuppes /usr/local/bin/fuppes
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'fuppesd' '/usr/local/bin/fuppesd'
/usr/bin/install -c .libs/fuppesd /usr/local/bin/fuppesd
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/tim/Desktop/fuppes/src'
make[2]: Leaving directory `/home/tim/Desktop/fuppes/src'
make[1]: Leaving directory `/home/tim/Desktop/fuppes/src'
Making install in src/gnome
make[1]: Entering directory `/home/tim/Desktop/fuppes/src/gnome'
make[2]: Entering directory `/home/tim/Desktop/fuppes/src/gnome'
test -z "/usr/local/libexec" || /bin/mkdir -p "/usr/local/libexec"
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
make[2]: Leaving directory `/home/tim/Desktop/fuppes/src/gnome'
make[1]: Leaving directory `/home/tim/Desktop/fuppes/src/gnome'
make[1]: Entering directory `/home/tim/Desktop/fuppes'
make[2]: Entering directory `/home/tim/Desktop/fuppes'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tim/Desktop/fuppes'
make[1]: Leaving directory `/home/tim/Desktop/fuppes'

```

can someone help me out?

---

### Post by timstone on 2008-10-05
ill bump this til it gets answered....i know mostly everyone has more experience with this stuff than me........im going to eat dinner, ill come back and hopefully my problem is solved

---

