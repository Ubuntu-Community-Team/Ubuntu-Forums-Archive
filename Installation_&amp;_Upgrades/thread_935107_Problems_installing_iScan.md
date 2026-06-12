---
title: "Problems installing iScan"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by jamespetts on 2008-10-01
I have recently downloaded the iScan scanning software for an Epson Perfection V700 photo. There is no .deb file for iScan, so I have had to compile it from source. I downloaded the file and followed the instructions. 

I had some errors, but I was able to resolve some of them by reading [this](http://ubuntuforums.org/archive/index.php/t-522253.html) thread. However, I then encountered a further error not addressed in that thread. When I executed "make install" (either as sudo or normal user), I received the following output:

```
$ sudo make install
Making install in include
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/include'
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/include'
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/include'
Making install in libltdl
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/libltdl'
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/libltdl'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/libltdl'
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/libltdl'
Making install in lib
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/lib'
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/lib'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/lib'
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/lib'
Making install in sanei
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/sanei'
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/sanei'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/sanei'
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/sanei'
Making install in backend
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/backend'
make  install-am
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/backend'
make[3]: Entering directory `/home/james/downloads/iscan-2.11.0/backend'
test -z "/usr/local/lib/sane" || mkdir -p -- "/usr/local/lib/sane"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libsane-epkowa.la' '/usr/local/lib/sane/libsane-epkowa.la'
/usr/bin/install -c .libs/libsane-epkowa.so.1.0.15 /usr/local/lib/sane/libsane-epkowa.so.1.0.15
(cd /usr/local/lib/sane && { ln -s -f libsane-epkowa.so.1.0.15 libsane-epkowa.so.1 || { rm -f libsane-epkowa.so.1 && ln -s libsane-epkowa.so.1.0.15 libsane-epkowa.so.1; }; })
(cd /usr/local/lib/sane && { ln -s -f libsane-epkowa.so.1.0.15 libsane-epkowa.so || { rm -f libsane-epkowa.so && ln -s libsane-epkowa.so.1.0.15 libsane-epkowa.so; }; })
/usr/bin/install -c .libs/libsane-epkowa.lai /usr/local/lib/sane/libsane-epkowa.la
/usr/bin/install -c .libs/libsane-epkowa.a /usr/local/lib/sane/libsane-epkowa.a
chmod 644 /usr/local/lib/sane/libsane-epkowa.a
ranlib /usr/local/lib/sane/libsane-epkowa.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/sane
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/sane

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
make  install-exec-hook
make[4]: Entering directory `/home/james/downloads/iscan-2.11.0/backend'
rm -f /usr/local/lib/sane/libsane.so.1
make[4]: Leaving directory `/home/james/downloads/iscan-2.11.0/backend'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/james/downloads/iscan-2.11.0/backend'
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/backend'
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/backend'
Making install in non-free
make[1]: Entering directory `/home/james/downloads/iscan-2.11.0/non-free'
make[2]: Entering directory `/home/james/downloads/iscan-2.11.0/non-free'
rm -f libesmod.so
rm: cannot remove `libesmod.so': Permission denied
make[2]: [libesmod.so] Error 1 (ignored)
case i686 in \
	  i?86) arch=i386;; \
	  *)	echo "unsupported architecture" 1>&2; \
		exit 1;; \
	esac; \
	ln -s ./libesmod-${arch}.c2.so libesmod.so
ln: creating symbolic link `libesmod.so': File exists
make[2]: *** [libesmod.so] Error 1
make[2]: Leaving directory `/home/james/downloads/iscan-2.11.0/non-free'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/james/downloads/iscan-2.11.0/non-free'
make: *** [install-recursive] Error 1
$
```

I cannot for the life of me understand why this is going wrong. Can anybody assist?

---

### Post by jamespetts on 2008-10-01
I have now managed to install iScan and get my scanner working using the technique described [here](http://www.avasys.jp/cgi-bin/lx/bbs/en/scanner-bbs/hyperbbs.cgi?mode=view;Code=5063), and the workaround described [here](https://bugs.launchpad.net/ubuntu/+bug/208405).

---

