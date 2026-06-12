---
title: "Broken dependencies"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by vorlket on 2013-03-01
After forcing version of libssl1.0.0 from 1.0.1-4ubuntu5.5 to 1.0.1-4ubuntu3 (to install python2.7-dev), I ended up with the following broken dependencies identified by Synaptic Package Manager


[TABLE="width: 500"]
[TR]
[TD]Package
[/TD]
[TD]Installed Version
[/TD]
[TD]Latest Version
[/TD]
[TD]Description
[/TD]
[/TR]
[TR]
[TD]acroread 
[/TD]
[TD]9.5.4-1precise1
[/TD]
[TD]9.5.4-1precise1
[/TD]
[TD]Adobe Reader
[/TD]
[/TR]
[TR]
[TD]libexpat1-dev
[/TD]
[TD]2.0.1-7ubuntu1
[/TD]
[TD]2.0.1-7.2ubuntu1
[/TD]
[TD]XML parsing C library - development kit
[/TD]
[/TR]
[TR]
[TD]libssl1.0.0
[/TD]
[TD]1.0.1-4ubuntu3
[/TD]
[TD]1.0.1-4ubuntu3
[/TD]
[TD]SSL shared libraries
[/TD]
[/TR]
[TR]
[TD]libssl1.0.0:i386
[/TD]
[TD]1.0.1-4ubuntu5.5
[/TD]
[TD]1.0.1-4ubuntu5.5
[/TD]
[TD]SSL shared libraries
[/TD]
[/TR]
[/TABLE]

Could you help me fixing the following broken dependencies related error?

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdbusmenu-qt2:i386 libopenal1:i386 bluez-alsa:i386 libsdl-ttf2.0-0:i386 libgconf-2-4:i386 libstdc++5:i386 libqt4-declarative:i386 libgail18:i386 libldap-2.4-2:i386 libao-common libv4l-0:i386 liblcms1:i386
  libqt4-qt3support:i386 libroken18-heimdal:i386 libunistring0:i386 libcupsimage2:i386 libgphoto2-port0:i386 libnss3:i386 libwrap0:i386 libcaca0:i386 gtk2-engines:i386 libgudev-1.0-0:i386 libsamplerate0:i386
  libcdparanoia0:i386 libcairo-gobject2:i386 libavc1394-0:i386 libdrm-radeon1:i386 libaio1:i386 libsane:i386 odbcinst1debian2 odbcinst1debian2:i386 libqt4-test:i386 libqt4-script:i386 libqt4-designer:i386
  libsdl-mixer1.2:i386 libqt4-network:i386 libqt4-dbus:i386 libxxf86vm1:i386 libcap2:i386 libproxy1:i386 ibus-gtk:i386 libdbus-glib-1-2:i386 libgl1-mesa-dri:i386 libtdb1:i386 libxcb-glx0:i386
  libasn1-8-heimdal:i386 libgl1-mesa-glx:i386 libspeex1:i386 libjack-jackd2-0:i386 libxslt1.1:i386 libgomp1:i386 libcapi20-3:i386 libibus-1.0-0:i386 libx11-xcb1:i386 libglapi-mesa:i386 odbcinst
  libgssapi3-heimdal:i386 libvisual-0.4-0:i386 libcanberra-gtk-module:i386 libcanberra0:i386 gtk2-engines-murrine:i386 libwavpack1:i386 libqt4-opengl:i386 libsoup-gnome2.4-1:i386 sni-qt:i386 libv4lconvert0:i386
  gstreamer0.10-plugins-good:i386 lib32gcc1 libqt4-xmlpatterns:i386 libiec61883-0:i386 libjson0:i386 libsdl-image1.2:i386 libdrm2:i386 libwind0-heimdal:i386 libsdl1.2debian:i386 libxaw7:i386 libgdbm3:i386
  libqtcore4:i386 libesd0:i386 libmikmod2:i386 acroread-common libdrm-nouveau1a:i386 libpulse-mainloop-glib0:i386 libtheora0:i386 libaa1:i386 libspeexdsp1:i386 libieee1284-3:i386 libdrm-intel1:i386 libao4:i386
  libxmu6:i386 libcanberra-gtk0:i386 libvorbisfile3:i386 libqt4-sql:i386 esound-common libasound2:i386 libxpm4:i386 libflac8:i386 libqt4-svg:i386 libusb-0.1-4:i386 libgail-common:i386 libhcrypto4-heimdal:i386
  liborc-0.4-0:i386 libraw1394-11:i386 libnspr4:i386 libshout3:i386 libdv4:i386 libhx509-5-heimdal:i386 libvorbisenc2:i386 libqt4-xml:i386 libasyncns0:i386 gstreamer0.10-x:i386 libgettextpo0:i386 libxss1:i386
  libgd2-xpm:i386 libheimbase1-heimdal:i386 libsdl-net1.2:i386 libvisual-0.4-plugins:i386 libgstreamer-plugins-base0.10-0:i386 libpciaccess0:i386 libgnome-keyring0:i386 libxtst6:i386 gtk2-engines-pixbuf:i386
  libqtgui4:i386 libtag1c2a:i386 libssl0.9.8:i386 libmpg123-0:i386 libmad0:i386 libsasl2-2:i386 gtk2-engines-oxygen:i386 lib32z1 xaw3dg:i386 libpulse0:i386 libheimntlm0-heimdal:i386 libpulsedsp:i386 lib32stdc++6
  libqt4-sql-mysql:i386 libodbc1:i386 libexif12:i386 libqt4-scripttools:i386 libglu1-mesa:i386 librtmp0:i386 libvorbis0a:i386 libqtwebkit4:i386 libgstreamer0.10-0:i386 libxp6:i386 libaudio2:i386 libxv1:i386
  gstreamer0.10-plugins-base:i386 libsndfile1:i386 libsqlite3-0:i386 libmng1:i386 libltdl7:i386 libkrb5-26-heimdal:i386 libasound2-plugins:i386 glib-networking:i386 libllvm3.0:i386 libsoup2.4-1:i386
  libgphoto2-2:i386 libogg0:i386 libtag1-vanilla:i386 libaudiofile1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acroread-bin:i386
Suggested packages:
  libldap2:i386 libgnome-speech7:i386
The following packages will be REMOVED:
  ia32-libs ia32-libs-multiarch:i386 libcurl3:i386 libexpat1-dev libsasl2-modules:i386 libssl1.0.0:i386 skype skype-bin:i386
The following NEW packages will be installed:
  acroread-bin:i386
0 upgraded, 1 newly installed, 8 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 60.1 MB of archives.
After this operation, 101 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.canonical.com/ubuntu/ precise/partner acroread-bin i386 9.5.4-1precise1 [60.1 MB]
Fetched 60.1 MB in 31s (1,899 kB/s)                                                                                                                                                                                 
E: Internal Error, No file name for libssl1.0.0
```

---

### Post by tgalati4 on 2013-03-01
It seems that acroread (Adobe Acrobat Reader) is only available in 32-bit.  So when you try to install it on a 64-bit system, it will pull in a boat load of 32-bit packages as well as the libraries to connect 32-bit code to a 64-bit machine.

Your 32-bit SSL library is newer than the 64-bit.  And the package manager (apt) is looking for the 5.5 library that every other package relies on.

In this situation, I would get the debian package *.deb for the correct SSL library and install it along side, so you have two copies of the library, but the package manager still has the correct one in the database.

The alternative is to download the source for Python-dev and compile it with the current 5.5 library, or ask the Python developers if there is a precompiled deb package that you can install as a work-around.  You are currently in *dependency file hell*.  Everything you do from now on is measured in *Agony Units*.

---

### Post by matt_symes on 2013-03-01
Hi

> E: Internal Error, No file name for libssl1.0.0

This is the second time i have seen this in the last couple of days. 

I'll take a look and see if i can find out why. That may not happen till the morning though.

What version of ubuntu are you using ? (i assume precise)

```
cat /etc/lsb-release
```

We'll also have a look at those dependenciy issues.

It's 4.30am here :)

Kind regards

---

### Post by vorlket on 2013-03-02
How do I compile a package with a particular library? Python-dev with the current 5.5 library in this particular case, but wanna learn how to in general.

```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
```

---

### Post by schragge on 2013-03-02
In general, you do it like this
```

sudo apt-get install [COLOR=red]your_library[/COLOR]-dev=[COLOR=red]specific_version[/COLOR]
fakeroot apt-get source -b [COLOR=red]your_package[/COLOR]

```

---

### Post by vorlket on 2013-03-03
Okay. As I understand, I have to install debian package for libssl1.0.0 version 5.5

```
$ sudo dpkg -i libssl1.0.0_1.0.1-4ubuntu5.5_amd64.deb
(Reading database ... 267248 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu3 (using libssl1.0.0_1.0.1-4ubuntu5.5_amd64.deb) ...
Unpacking replacement libssl1.0.0 ...
dpkg: error processing libssl1.0.0_1.0.1-4ubuntu5.5_amd64.deb (--install):
 './usr/share/doc/libssl1.0.0/changelog.Debian.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 libssl1.0.0_1.0.1-4ubuntu5.5_amd64.deb

```

did i miss something?

---

### Post by vorlket on 2013-03-03
arggghhh.... darn it. just gonna reinstall the whole thing for the time being. thanks for all the help, appreciate it!

matt_symes: when you find out what the issues are, could you let me know? i am interested in finding out, but got bills to pay! :) thanks.

---

