---
title: "[SOLVED] GTK problem"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by kinngg on 2007-08-04
checking for zlib.h >= 1.1.4... no
checking for zlib.h... (cached) no
configure: WARNING: zlib library not found or too old, will use built-in instead
checking for png.h > 0.90... no
checking for png.h... (cached) no
configure: WARNING: system png library not found or too old, will use built-in instead
checking for jpeglib.h... no
configure: WARNING: system jpeg library not found, will use built-in instead
checking tiffio.h usability... no
checking tiffio.h presence... no
checking for tiffio.h... no
configure: WARNING: system tiff library not found, will use built-in instead
checking expat.h usability... no
checking expat.h presence... no
checking for expat.h... no
configure: WARNING: system expat library not found, will use built-in instead
checking mspack.h usability... no
checking mspack.h presence... no
checking for mspack.h... no
checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

after i tried to compile amule, by ./configure i get this.. why/

---

### Post by taurus on 2007-08-04
Because you need the dev package for gtk+ before you can build something from source.  

Fire up synaptic and search for libgtk+-dev package and install it.

p.s.  What are you trying to build anyway?

---

### Post by kinngg on 2007-08-04
im tryin 2 build amule

---

### Post by yabbadabbadont on 2007-08-04
It is already in the repositories.  Unless you need a newer version, I would suggest that you just install the one from there.

```
/home/daffy $ aptitude show amule
Package: amule
State: not installed
Version: 2.1.3-1ubuntu2
Priority: optional
Section: universe/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 3535k
Depends: amule-common (= 2.1.3-1ubuntu2), libc6 (>= 2.5-0ubuntu1), libcrypto++5.2c2a, libgcc1 (>= 1:4.1.2), libstdc++6 (>=
         4.1.2), libwxbase2.8-0 (>= 2.8.1.1), libwxgtk2.8-0 (>= 2.8.1.1), zlib1g (>= 1:1.2.1)
Recommends: amule-utils
Suggests: amule-utils-gui
Description: client for the eD2k and Kad networks, like eMule
 aMule is a peer-to-peer file sharing application, designed to connect to the eDonkey and Kad networks. It has a wide range of
 features, including many of the original eMule client, like: 
 
 * online signature, source exchange, compressed transfers, secure identification, and IP filter support 
 * boolean search, which can be local, global, or in the Kad network 
 * checks against aggressive clients 
 * slot allocation, to decide the number of remote clients 
 * systray works well both in GNOME and KDE 
 * translations to many languages 
   
 A daemonized version of the application that does not need a graphic environment to run is available in the amule-daemon
 package, and various utilities of interest can be found in the amule-utils and amule-utils-gui packages, including the ed2k
 link hander. 
 
 Homepage: http://www.amule.org

```
As this output shows, it is in the universe repository, so you will need to enable it if you haven't already.

---

