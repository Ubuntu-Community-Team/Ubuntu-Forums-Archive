---
title: "Problem with glib instalation"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by Aster.Orthrinos on 2012-02-04
I have Ubuntu Studio 11.04 with all updates on this day. 

I needed to install glib as dependency of GTK. I have downloaded and installed glib-2.30.2 with convential method from INSTALL file:

```
./config
make
rm -rf /install-prefix/include/glib.h /install-prefix/include/gmodule.h
sudo make install

```After this I tried to install atk-2.0.1 where I stoped on ./configure step with following messages:

```
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.30.2, but GLIB (2.28.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: 
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```Intalling with method from [http://www.linuxfromscratch.org/blfs/view/svn/general/glib2.html:](http://www.linuxfromscratch.org/blfs/view/svn/general/glib2.html:)

```
 PCRE_LIBS=-lpcre  PCRE_CFLAGS=" "  LIBFFI_LIBS=-lffi LIBFFI_CFLAGS=-I/usr/lib/libffi-3.0.10/include ./configure --prefix=/usr --sysconfdir=/etc --with-pcre=system 
make
make install
ln -v -sfn ../../lib/glib-2.0/include/glibconfig.h /usr/include/glib-2.0/glibconfig.h

```gave same result. Please help.

---

### Post by Aster.Orthrinos on 2012-02-04
I've found decision on [http://opennet.ru/openforum/vsluhforumID15/1229.html](http://opennet.ru/openforum/vsluhforumID15/1229.html) . It is:

```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig LD_LIBRARY_PATH=/usr/local/lib:/usr/lib ./configure
``` 

Note that I have installed glib with second method from site mentioned in first post which requires           PCRE (it's installing described on same site), but I do not now if it gave something.

---

