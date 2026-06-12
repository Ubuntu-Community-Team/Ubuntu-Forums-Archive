---
title: "ia32-libs needs bluez-alsa?"
date: 2012-09-16
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-09-16
I'd like to know why bluez-alsa is a dependency for ia32-libs when it is not so for a normal system.  Why would multilib need this (and a few other packages it drags in).

---

### Post by jerrrys on 2012-09-16
Im not seeing this dependency issue.

[http://packages.ubuntu.com/precise/ia32-libs](http://packages.ubuntu.com/precise/ia32-libs)

---

### Post by Skaperen on 2012-09-16
It's in 12.04 ...
```
Package: **ia32-libs**
Priority: optional
Section: universe/libs
Installed-Size: 40
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 20090808ubuntu35
Provides: ia32-libs-gtk, ia32-libs-sdl, lib32v4l-0
Depends: **ia32-libs-multiarch**
Breaks: flashplugin-installer (<< 10.3.183.4ubuntu4), nspluginwrapper (<< 1.4.4-0ubuntu2)
Filename: pool/universe/i/ia32-libs/ia32-libs_20090808ubuntu35_amd64.deb
Size: 3362
MD5sum: d6a9b3017c6aca27c39488ed28398c88
SHA1: f40d0c86f82b13ec6f88a0555abb3def19fd66c8
SHA256: 803e8c085876f8c406ea26e1f716b3e30998da37d47568ad6354a208cb0a8295
Description: ia32 shared libraries - transitional package
Description-md5: abea08296eb03bbfec6601033318c72a
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
``````
Package: **ia32-libs-multiarch**
Priority: extra
Section: universe/libs
Installed-Size: 39
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ia32-libs
Version: 20090808ubuntu35
Depends: **bluez-alsa**, libgettextpo0, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-fluendo-mp3, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-oxygen, gvfs, ibus-gtk, libacl1, libaio1, libao4, libasound2, libasound2-plugins, libasyncns0, libattr1, libaudio2, libcanberra-gtk-module, libcap2, libcapi20-3, libcups2, libcupsimage2, libcurl3, libdbus-glib-1-2, libesd0, libfontconfig1, libfreetype6, libgail-common, libgconf-2-4, libgdbm3, libglapi-mesa, libglu1-mesa, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libmpg123-0, libncursesw5, libnspr4, libnss3, libodbc1, libopenal1, libpulse-mainloop-glib0, libqt4-dbus, libqt4-network, libqt4-opengl, libqt4-qt3support, libqt4-script, libqt4-scripttools, libqt4-sql, libqt4-svg, libqt4-test, libqt4-xml, libqt4-xmlpatterns, libqtcore4, libqtgui4, libqtwebkit4, librsvg2-common, libsane, libsdl-mixer1.2, libsdl-image1.2, libsdl-net1.2, libsdl-ttf2.0-0, libsdl1.2debian, libsqlite3-0, libssl0.9.8, libssl1.0.0, libstdc++5, libstdc++6, libxaw7, libxml2, libxp6, libxslt1.1, libxss1, libxtst6, odbcinst1debian2, libpulsedsp, xaw3dg
Recommends: libgl1-mesa-glx, libgl1-mesa-dri
Suggests: libpam-ldap, libpam-winbind, libnss-ldap
Filename: pool/universe/i/ia32-libs/ia32-libs-multiarch_20090808ubuntu35_i386.deb
Size: 4554
MD5sum: cda17f80e8c2c7e8ed79390c6462d184
SHA1: 108d0a21f7889331105afeb0a86dad9f3da2d90c
SHA256: 93045368d952407c927000ec582b573bf27b367cc13a06d8a9a6f786dd7818e4
Description: Multi-arch versions of former ia32-libraries
Multi-Arch: foreign
Description-md5: 2dfb3546bc498438a76638f4fcd00b0c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```And when I true to remove bluez-alsa I get:```
Script started on Sun 16 Sep 2012 06:49:41 PM UTC
18:49:41 [12149] EXECUTING: time ( apt-get remove **bluez-alsa bluez-alsa:i386** )
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bluez-alsa is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libopenal1:i386 sound-theme-freedesktop libsdl-ttf2.0-0:i386 libkrb5-3:i386 libgconf-2-4:i386 libatk1.0-0:i386 libk5crypto3:i386 libstdc++5:i386 libstdc++6:i386 libxfixes3:i386 libqt4-declarative:i386 libxcomposite1:i386 libgail18:i386
  libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386 libqt4-qt3support:i386 libroken18-heimdal:i386 libunistring0:i386 libcupsimage2:i386 libgphoto2-port0:i386 libidn11:i386 libnss3:i386 libwrap0:i386 libcaca0:i386
  gtk2-engines:i386 libgudev-1.0-0:i386 libsamplerate0:i386 libjpeg-turbo8:i386 libcdparanoia0:i386 libcairo-gobject2:i386 libavc1394-0:i386 libjpeg8:i386 qdbus glib-networking-common libaio1:i386 libsane:i386 odbcinst1debian2:i386
  libqt4-test:i386 libqt4-script:i386 libqt4-designer:i386 libsdl-mixer1.2:i386 libqt4-network:i386 libqt4-dbus libqt4-dbus:i386 libxxf86vm1:i386 libcap2:i386 libproxy1 libproxy1:i386 ibus-gtk:i386 libdbus-glib-1-2:i386
  libgl1-mesa-dri:i386 libtdb1:i386 libxcb-glx0:i386 libasn1-8-heimdal:i386 libgl1-mesa-glx:i386 libspeex1:i386 gvfs-libs:i386 gconf2 libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386 libcapi20-3:i386 libibus-1.0-0:i386 libcairo2:i386
  libx11-xcb1:i386 libgnutls26:i386 libglapi-mesa:i386 libopenal-data libgssapi3-heimdal:i386 libvisual-0.4-0:i386 bluez libcanberra-gtk-module:i386 libcanberra0:i386 libtasn1-3:i386 libfreetype6:i386 gtk2-engines-murrine:i386
  libwavpack1:i386 libqt4-opengl:i386 libsoup-gnome2.4-1:i386 libmysqlclient18:i386 libexpat1:i386 libv4lconvert0:i386 gstreamer0.10-plugins-good:i386 libqt4-xmlpatterns:i386 librsvg2-common:i386 libdatrie1:i386 libavahi-common-data:i386
  libiec61883-0:i386 libjson0:i386 libgdk-pixbuf2.0-0:i386 libsdl-image1.2:i386 libxcb1:i386 libp11-kit0:i386 libwind0-heimdal:i386 libxau6:i386 libpixman-1-0:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386 libcups2:i386
  libcurl3:i386 libqtcore4 libqtcore4:i386 libxinerama1:i386 libesd0:i386 libmikmod2:i386 libkrb5support0:i386 libxft2:i386 libcroco3:i386 libpulse-mainloop-glib0:i386 libtheora0:i386 libice6:i386 libaa1:i386 libspeexdsp1:i386
  libxdmcp6:i386 libieee1284-3:i386 libgcrypt11:i386 libthai0:i386 libxml2:i386 libao4:i386 libkeyutils1:i386 libxmu6:i386 libcanberra-gtk0:i386 libvorbisfile3:i386 libqt4-sql:i386 esound-common libasound2:i386 libxpm4:i386 libflac8:i386
  libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386 libxrender1:i386 libhcrypto4-heimdal:i386 liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 libqt4-xml
  libqt4-xml:i386 libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386 libgd2-xpm:i386 libheimbase1-heimdal:i386 libtiff4:i386 libsdl-net1.2:i386 libjasper1:i386 libvisual-0.4-plugins:i386
  libgstreamer-plugins-base0.10-0:i386 libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386 gsettings-desktop-schemas libqtgui4:i386 libtag1c2a:i386 librsvg2-2:i386 libavahi-client3:i386 libssl0.9.8:i386 libmpg123-0:i386
  libmad0:i386 libx11-6:i386 libsasl2-2:i386 gtk2-engines-oxygen:i386 libfontconfig1:i386 xaw3dg:i386 libpango1.0-0:i386 libsm6:i386 libpulse0:i386 libheimntlm0-heimdal:i386 libpulsedsp:i386 libxdamage1:i386 gvfs:i386
  libqt4-sql-mysql:i386 libxcb-render0:i386 libodbc1:i386 libexif12:i386 libqt4-scripttools:i386 libglu1-mesa:i386 librtmp0:i386 libgssapi-krb5-2:i386 libxi6:i386 libvorbis0a:i386 libqtwebkit4:i386 glib-networking-services
  libgstreamer0.10-0:i386 libxp6:i386 libaudio2:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386 libxv1:i386 libxext6:i386 libsasl2-modules:i386 libavahi-common3:i386 mysql-common libxrandr2:i386 gstreamer0.10-plugins-base:i386
  libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libgtk2.0-0:i386 libltdl7:i386 libkrb5-26-heimdal:i386 libasound2-plugins:i386 glib-networking glib-networking:i386 libgpg-error0:i386 libllvm3.0:i386 libsoup2.4-1:i386 libgphoto2-2:i386
  libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  **bluez-alsa:i386 _ia32-libs ia32-libs-multiarch:i386_**
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 462 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```
I want to remove it w/o removing the ia32-libs that I believe should not need it (64-bit doesn't).

---

### Post by jerrrys on 2012-09-16
My bad.  It is a dependency for ia32-libs-multiarch.  Looks to me that your stuck with it.

[http://packages.ubuntu.com/precise/ia32-libs-multiarch](http://packages.ubuntu.com/precise/ia32-libs-multiarch)

---

### Post by Skaperen on 2012-09-17
> **jerrrys said:**
> My bad.  It is a dependency for ia32-libs-multiarch.  Looks to me that your stuck with it.

[http://packages.ubuntu.com/precise/ia32-libs-multiarch](http://packages.ubuntu.com/precise/ia32-libs-multiarch)
Yes, that, and many other things that don't make sense.

Maybe ia32-libs is not a meta package for specific multilib, but rather a catch-all that people MAY use to set up some sort of multilib.  Some of the packages like bluez-alsa are being brought in AS A DEPENDENCY when they are NOT dependencies in either a 32-bit or 64-bit single architecture install.

This appears to reveal a deficiency in the packaging logic.  If I install Ubuntu 12.04 I do get bluez-alsa.  But I can simply remove it and it will go away (I have done so because I don't need it).  But ia32-libs creates a dependency that was not there before.  This is not how it should be.  The ia32-libs package (or subpackages it brings in) should not DEPEND on certain other packages, but instead, bring them in by default the same way installing Ubuntu does (by whatever means that happens to be) so that if these packages that are not needed do not create that "impossible situation" when they are excluded at the same time, or can be removed later without it trying to revert the whole thing back.

An interesting point here is that by installing ia32-libs one ends up with a number of programs on a 64-bit system that are in their 32-bit version.  So ia32-libs is not just a means to allow 32-bit dynamically linked programs to run, it actually creates a mixed system.

So what I really need to do is find what ACTUAL libraries the program(s) I need to run depend on, and just install those.  That or install a 32-bit system, instead.  Any suggestions on that?  The program I need to run is the Android Emulator which is not in a .deb package, and has no 64-bit version (I guess Google is still way behind the curve in software development).

---

### Post by jerrrys on 2012-09-17
Don't know if this will help you any, but got some hits [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=android+emulator&as_qdr=all&sa=Google+Search&lang=en")

Good luck :)

---

