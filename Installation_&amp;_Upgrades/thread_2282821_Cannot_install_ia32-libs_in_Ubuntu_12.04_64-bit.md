---
title: "Cannot install ia32-libs in Ubuntu 12.04 64-bit"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by marjan2 on 2015-06-17
Hi, 

I am trying to install ia32-libs in my Ubuntu 12.04 64-bit for some Canon printer drivers to work correctly.

When I execute:

sudo apt-get install ia32-libs

I get following output:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-fluendo-mp3:i386 gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs-multiarch:i386
  ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao-common libao4:i386 libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2 libaudio2:i386
  libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386
  libbz2-1.0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386
  libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2
  libcomerr2:i386 libcroco3:i386 libcups2 libcups2:i386 libcupsimage2 libcupsimage2:i386 libcurl3 libcurl3:i386
  libdatrie1:i386 libdb5.1:i386 libdbus-1-3 libdbus-1-3:i386 libdbus-glib-1-2 libdbus-glib-1-2:i386 libdrm-dev
  libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386 libdrm-nouveau2 libdrm-radeon1
  libdrm-radeon1:i386 libdrm2 libdrm2:i386 libdv4:i386 libelf1 libelf1:i386 libesd0:i386 libexif12 libexif12:i386
  libexpat1 libexpat1:i386 libexpat1-dev libffi6:i386 libflac8 libflac8:i386 libfontconfig1:i386 libfreetype6
  libfreetype6:i386 libgail-3-0 libgail-common:i386 libgail18:i386 libgconf-2-4:i386 libgcrypt11 libgcrypt11:i386
  libgcrypt11-dev libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386
  libglib2.0-0:i386 libglu1-mesa libglu1-mesa:i386 libglu1-mesa-dev libgnome-keyring0:i386 libgnutls26
  libgnutls26:i386 libgomp1:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386
  libgssapi-krb5-2 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0:i386 libgudev-1.0-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libibus-1.0-0:i386 libice6:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386
  libjasper1 libjasper1:i386 libjpeg-turbo8 libjpeg-turbo8:i386 libjpeg8:i386 libjson0 libjson0:i386 libk5crypto3
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3 libkrb5-3:i386 libkrb5support0
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2 libldap-2.4-2:i386 libllvm3.0:i386 libltdl7:i386 libmad0:i386
  libmikmod2:i386 libmng1:i386 libmpg123-0:i386 libmysqlclient18 libmysqlclient18:i386 libncurses5:i386
  libncursesw5:i386 libnspr4 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386 liboil0.3:i386 libopenal1:i386
  liborc-0.4-0:i386 libp11-kit0:i386 libpango1.0-0:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0
  libpixman-1-0:i386 libpng12-0:i386 libproxy1 libproxy1:i386 libproxy1-plugin-gsettings
  libproxy1-plugin-networkmanager libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386 libqt4-dbus
  libqt4-dbus:i386 libqt4-declarative libqt4-declarative:i386 libqt4-designer libqt4-designer:i386 libqt4-help
  libqt4-network libqt4-network:i386 libqt4-opengl libqt4-opengl:i386 libqt4-qt3support libqt4-qt3support:i386
  libqt4-script libqt4-script:i386 libqt4-scripttools libqt4-scripttools:i386 libqt4-sql libqt4-sql:i386
  libqt4-sql-mysql libqt4-sql-mysql:i386 libqt4-sql-sqlite libqt4-svg libqt4-svg:i386 libqt4-test libqt4-test:i386
  libqt4-xml libqt4-xml:i386 libqt4-xmlpatterns libqt4-xmlpatterns:i386 libqtcore4 libqtcore4:i386 libqtgui4
  libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386 libroken18-heimdal:i386 librsvg2-2 librsvg2-2:i386
  librsvg2-common librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386
  libsdl1.2debian libsdl1.2debian:i386 libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386
  libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl-dev
  libssl0.9.8:i386 libssl1.0.0 libssl1.0.0:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3 libtasn1-3:i386
  libtdb1:i386 libthai0:i386 libtheora0:i386 libtiff4 libtiff4:i386 libtinfo5:i386 libudev0:i386
  libunistring0:i386 libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386
  libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386
  libwind0-heimdal:i386 libwrap0:i386 libx11-6 libx11-6:i386 libx11-dev libx11-xcb1 libx11-xcb1:i386 libxau6:i386
  libxaw7:i386 libxcb-glx0 libxcb-glx0:i386 libxcb-render0 libxcb-render0:i386 libxcb-shm0 libxcb-shm0:i386
  libxcb1 libxcb1:i386 libxcb1-dev libxcomposite1:i386 libxcursor1 libxcursor1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext-dev libxext6 libxext6:i386 libxfixes3 libxfixes3:i386 libxft2:i386 libxi6 libxi6:i386
  libxinerama1 libxinerama1:i386 libxml2 libxml2:i386 libxmu6:i386 libxp6 libxp6:i386 libxpm4:i386 libxrandr2
  libxrandr2:i386 libxrender1 libxrender1:i386 libxslt1.1 libxslt1.1:i386 libxss1:i386 libxt-dev libxt6
  libxt6:i386 libxtst6 libxtst6:i386 libxv1 libxv1:i386 libxxf86vm1 libxxf86vm1:i386 mesa-common-dev mysql-common
  odbcinst1debian2:i386 qdbus xaw3dg:i386 zlib1g:i386
Suggested packages:
  murrine-themes:i386 kde-config-gtk-style:i386 libpam-ldap:i386 libpam-winbind:i386 libnss-ldap:i386
  libroar1:i386 libsndio0:i386 roaraudio-server:i386 libasound2-python:i386 nas nas:i386 libcanberra-pulse:i386
  cups-common:i386 libdv-bin:i386 pulseaudio-esound-compat:i386 rng-tools rng-tools:i386 libgcrypt11-doc
  libgd-tools:i386 libglide3 libglide3:i386 gnome-keyring:i386 gnutls-bin gnutls-bin:i386 gphoto2:i386 gtkam:i386
  gpm:i386 krb5-doc krb5-user krb5-doc:i386 krb5-user:i386 gstreamer-codec-install:i386 gnome-codec-install:i386
  gstreamer0.10-tools:i386 jackd2:i386 libjasper-runtime libjasper-runtime:i386 liblcms-utils:i386 libmyodbc:i386
  odbc-postgresql:i386 tdsodbc:i386 unixodbc-bin:i386 ttf-baekmuk:i386 ttf-arphic-gbsn00lp:i386
  ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386 ttf-arphic-bkai00mp:i386 libqt4-declarative-folderlistmodel
  libqt4-declarative-gestures libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-declarative-folderlistmodel:i386 libqt4-declarative-gestures:i386 libqt4-declarative-particles:i386
  libqt4-declarative-shaders:i386 qt4-qmlviewer:i386 libqt4-dev libqt4-dev:i386 qt4-qtconfig qt4-qtconfig:i386
  libraw1394-doc:i386 librsvg2-bin librsvg2-bin:i386 hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386 libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386 speex:i386 libxcb-doc
Recommended packages:
  xml-core:i386
The following packages will be REMOVED:
  flashplugin-installer libnspr4-0d
The following NEW packages will be installed:
  bluez-alsa:i386 glib-networking:i386 gstreamer0.10-fluendo-mp3:i386 gstreamer0.10-plugins-base:i386
  gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386
  gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs:i386 gvfs-libs:i386 ia32-libs ia32-libs-multiarch:i386
  ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao-common libao4:i386 libasn1-8-heimdal:i386
  libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2:i386
  libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386
  libbz2-1.0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386
  libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386
  libcroco3:i386 libcups2:i386 libcupsimage2:i386 libcurl3:i386 libdatrie1:i386 libdb5.1:i386 libdbus-1-3:i386
  libdbus-glib-1-2:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-nouveau2 libdrm-radeon1:i386 libdrm2:i386
  libdv4:i386 libelf1:i386 libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgail-common:i386 libgail18:i386 libgconf-2-4:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dri:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgnome-keyring0:i386
  libgnutls26:i386 libgomp1:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgpm2:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libgtk2.0-0:i386 libgudev-1.0-0:i386 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386 libibus-1.0-0:i386 libice6:i386 libidn11:i386
  libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjson0:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386
  liblcms1:i386 libldap-2.4-2:i386 libllvm3.0:i386 libltdl7:i386 libmad0:i386 libmikmod2:i386 libmng1:i386
  libmpg123-0:i386 libmysqlclient18:i386 libncurses5:i386 libncursesw5:i386 libnspr4:i386 libnss3:i386
  libodbc1:i386 libogg0:i386 liboil0.3:i386 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpango1.0-0:i386
  libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386
  libpulse0:i386 libpulsedsp:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386
  libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386
  libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386
  libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386 libroken18-heimdal:i386 librsvg2-2:i386
  librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386
  libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386
  libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0:i386
  libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386 libtheora0:i386 libtiff4:i386
  libtinfo5:i386 libudev0:i386 libunistring0:i386 libusb-0.1-4:i386 libuuid1:i386 libv4l-0:i386
  libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386
  libvorbisfile3:i386 libwavpack1:i386 libwind0-heimdal:i386 libwrap0:i386 libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxaw7:i386 libxcb-glx0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386 libxcomposite1:i386
  libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxft2:i386 libxi6:i386
  libxinerama1:i386 libxml2:i386 libxmu6:i386 libxp6:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386
  libxslt1.1:i386 libxss1:i386 libxt6:i386 libxtst6:i386 libxv1:i386 libxxf86vm1:i386 odbcinst1debian2:i386
  xaw3dg:i386 zlib1g:i386
The following packages will be upgraded:
  libaudio2 libcomerr2 libcups2 libcupsimage2 libcurl3 libdbus-1-3 libdbus-glib-1-2 libdrm-dev libdrm-intel1
  libdrm-nouveau1a libdrm-radeon1 libdrm2 libelf1 libexif12 libexpat1 libexpat1-dev libflac8 libfreetype6
  libgail-3-0 libgcrypt11 libgcrypt11-dev libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglu1-mesa libglu1-mesa-dev libgnutls26 libgssapi-krb5-2 libgtk-3-0 libgtk-3-bin libgtk-3-common libjasper1
  libjpeg-turbo8 libjson0 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 libmysqlclient18 libnspr4
  libpixman-1-0 libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script
  libqt4-scripttools libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 librsvg2-2 librsvg2-common libsdl1.2debian libssl-dev libssl1.0.0
  libtasn1-3 libtiff4 libx11-6 libx11-dev libx11-xcb1 libxcb-glx0 libxcb-render0 libxcb-shm0 libxcb1 libxcb1-dev
  libxcursor1 libxext-dev libxext6 libxfixes3 libxi6 libxinerama1 libxml2 libxp6 libxrandr2 libxrender1 libxslt1.1
  libxt-dev libxt6 libxtst6 libxv1 libxxf86vm1 mesa-common-dev mysql-common qdbus
97 upgraded, 235 newly installed, 2 to remove and 399 not upgraded.
Need to get 35.0 MB/106 MB of archives.
After this operation, 233 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://security.ubuntu.com/ubuntu/ precise-security/main libssl-dev amd64 1.0.1-4ubuntu5.27
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libssl1.0.0 amd64 1.0.1-4ubuntu5.27
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libssl1.0.0 i386 1.0.1-4ubuntu5.27
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libcups2 amd64 1.5.3-0ubuntu8.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libcups2 i386 1.5.3-0ubuntu8.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libcupsimage2 amd64 1.5.3-0ubuntu8.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libcupsimage2 i386 1.5.3-0ubuntu8.6
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-sql-sqlite amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-sql-mysql amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-qt3support amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-help amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-svg amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-scripttools amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-opengl amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-designer amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqtgui4 amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-declarative amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-sql amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-xmlpatterns amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-network amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-script amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-test amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main qdbus amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-dbus amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-xml amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqtcore4 amd64 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqtcore4 i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-xml i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-dbus i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-network i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-script i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-sql i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-xmlpatterns i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqtgui4 i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-declarative i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-designer i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-opengl i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-qt3support i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-scripttools i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-sql-mysql i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-svg i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ precise-security/main libqt4-test i386 4:4.8.1-0ubuntu4.5
  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_1.0.1-4ubuntu5.27_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5.27_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5.27_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.3-0ubuntu8.6_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.3-0ubuntu8.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.3-0ubuntu8.6_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.3-0ubuntu8.6_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-sqlite_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-help_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/qdbus_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.8.1-0ubuntu4.5_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xml_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-dbus_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-script_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-xmlpatterns_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-declarative_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-designer_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-qt3support_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-scripttools_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-sql-mysql_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-svg_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-test_4.8.1-0ubuntu4.5_i386.deb  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

What I have to do to install ia32-libs?

Thank you for your help.

Kind regards,
Marjan

---

### Post by dino99 on 2015-06-17
The ia32-libs package was a hack to get 32-bit packages installed on a 64-bit installation. Since Ubuntu version 11.10 (Oneiric), Multi Arch has been added. One of the objectives for it is removing the ia32-libs package. Instead, you have to install the 32-bit libraries of a package with:

> sudo apt-get install package-name:i386

---

### Post by marjan2 on 2015-06-17
I tried following command after [COLOR=#000000]dino99's suggestions:
[/COLOR]
[COLOR=#000000]*sudo apt-get install *[/COLOR]*ia32-libs*[COLOR=#000000][I]:i386

[/I][/COLOR]I got following output:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package ia32-libs:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0 lib32asound2


E: Package 'ia32-libs:i386' has no installation candidate

```

Still cannot install ia32-libs. What to do from here?

Marjan

---

### Post by cooleryawner on 2015-06-17
Why do you need i386 libs exactly?

---

### Post by deadflowr on 2015-06-18
First, the ia32-libs package is a amd64(64-bit)package only, there is no i386(32-bit)package for it.

And second, you need to run an update so that you have access to the current packages.
Your output shows a lot of older versions of the packages, which are no longer available at the IP addresses shown.

Simply updating your system, will also update the list of available packages.
Use the system's update manager to get updated.

---

