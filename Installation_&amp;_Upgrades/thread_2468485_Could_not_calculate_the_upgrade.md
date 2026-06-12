---
title: "Could not calculate the upgrade"
date: 2021-10-31
forum: Installation &amp; Upgrades
---

### Post by peyre on 2021-10-31
These past two versions of *buntu I've been unable to upgrade to the latest version on my desktop.  Both laptops upgraded flawlessly, but on my desktop I get:

Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade.
This was likely caused by:
* Unofficial software packages not provided by Ubuntu

If this were one of the laptops I'd just wipe and reinstall, but my desktop is *much* more involved.  Lots of programs installed and configured.  I've seen several things people have suggested online to fix this, but none of them have helped me.

for instance, **grep Broken /var/log/dist-upgrade/apt.log** returns:

```
Broken libsrt1.4-gnutls:amd64 Breaks on libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK >
Broken libtss2-esys-3.0.2-0:amd64 Breaks on libtss2-esys0:amd64 < 3.0.1-1 @ii mK > (< 3.0.2-1)
Broken xfce4-helpers:amd64 Breaks on libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
Broken libsidplayfp5:amd64 Breaks on libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK >
Broken python2:amd64 PreDepends on python2-minimal:amd64 < none | 2.7.18-2 @un umH > (= 2.7.18-2)
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
Broken libboost1.74-dev:amd64 Conflicts on libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU >
Broken libmailutils6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2)
Broken libmu-dbm6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2)
Broken libexo-1-0:amd64 Depends on libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mR >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
Broken python2:amd64 PreDepends on python2-minimal:amd64 < none | 2.7.18-2 @un umH > (= 2.7.18-2)
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >

```

but when I **sudo apt-get remove listr1.4-gnutls**, it returns:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package listr1.4-gnutls
E: Couldn't find any package by glob 'listr1.4-gnutls'
E: Couldn't find any package by regex 'listr1.4-gnutls'
```

---

### Post by Impavidus on 2021-10-31
What release is this and to what release are you attempting to upgrade? And do you have software from other sources than the official Ubuntu repositories?

---

### Post by peyre on 2021-10-31
Oh sorry!  Should've thought to include that.  I'm on 20.10.

The amount of stuff I have installed on this machine is the reason this is such an issue.  For a start, I'm using Nvidia drivers since nouveau was causing it to crash or log me out spontaneously.

Software from outside the repository?  Nothing recent.  I think maybe everything on this machine is through the repositories, except Race Into Space and things I installed under Wine, but those have been on this machine for some time.

---

### Post by MAFoElffen on 2021-10-31
I think if you posted the /var/log/dist-upgrade/apt.log to an Ubuntu pastebin, it would reveal a bigger, more complete picture... That log tries to determine, from the installed packages, a plan on would it should do to resolve upgrades of packages. On what you did post, it showed what would be broken (mostly on Python 2 packages), but not on the packages it was tring to find an alternate path around, that started that decision...

Just saying, there are more details needed to see the picture of that.

---

### Post by peyre on 2021-10-31
Yeah, I thought it might be non-simple.  Here's my apt.log.

```
Log time: 2021-10-31 07:22:46.549160
Log time: 2021-10-31 07:22:48.314208
Log time: 2021-10-31 07:24:01.495812
  MarkDelete python-minimal:amd64 < 2.7.1-0ubuntu2 @ii mK NPb > FU=1
  MarkInstall python-is-python2:amd64 < none -> 2.7.18-9 @un umN Ib > FU=1
  Installing python2:amd64 as Depends of python-is-python2:amd64
    MarkInstall python2:amd64 < none -> 2.7.18-2 @un uN Ib > FU=0
    Installing python2-minimal:amd64 as PreDepends of python2:amd64
      MarkInstall python2-minimal:amd64 < none -> 2.7.18-2 @un uN > FU=0
    Installing libpython2-stdlib:amd64 as Depends of python2:amd64
      MarkInstall libpython2-stdlib:amd64 < none -> 2.7.18-2 @un uN > FU=0
Starting pkgProblemResolver with broken count: 0
Starting 2 pkgProblemResolver with broken count: 0
Done
    MarkKeep python-minimal:amd64 < 2.7.1-0ubuntu2 @ii R NPb > FU=0
  MarkInstall libunity-settings-daemon1:amd64 < 15.04.1+20.04.20200325-0ubuntu1 -> 15.04.1+20.04.20200325-0ubuntu2 @ii umU Ib > FU=0
  Installing libgdk-pixbuf-2.0-0:amd64 as Depends of libunity-settings-daemon1:amd64
    MarkInstall libgdk-pixbuf-2.0-0:amd64 < none -> 2.42.2+dfsg-1build1 @un uN > FU=0
  MarkInstall blender:amd64 < 2.83.5+dfsg-1build2 -> 2.83.5+dfsg-5build1 @ii umU Ib > FU=0
  Installing libboost-locale1.74.0:amd64 as Depends of blender:amd64
    MarkInstall libboost-locale1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN Ib > FU=0
    Installing libboost-thread1.74.0:amd64 as Depends of libboost-locale1.74.0:amd64
      MarkInstall libboost-thread1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN > FU=0
  Installing libopenimageio2.2:amd64 as Depends of blender:amd64
    MarkInstall libopenimageio2.2:amd64 < none -> 2.2.10.1+dfsg-1build1 @un uN Ib > FU=0
    Installing libboost-filesystem1.74.0:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libboost-filesystem1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN > FU=0
    Installing libdcmtk15:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libdcmtk15:amd64 < none -> 3.6.5-1 @un uN > FU=0
    Installing libopencv-core4.5:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libopencv-core4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
    Installing libopencv-imgproc4.5:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libopencv-imgproc4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
    Installing libopencv-videoio4.5:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libopencv-videoio4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
      Installing libopencv-imgcodecs4.5:amd64 as Depends of libopencv-videoio4.5:amd64
        MarkInstall libopencv-imgcodecs4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
        Installing libgdal28:amd64 as Depends of libopencv-imgcodecs4.5:amd64
          MarkInstall libgdal28:amd64 < none -> 3.2.2+dfsg-1ubuntu1 @un uN Ib > FU=0
          Installing libarmadillo10:amd64 as Depends of libgdal28:amd64
            MarkInstall libarmadillo10:amd64 < none -> 1:10.1.2+dfsg-4build1 @un uN > FU=0
          Installing libdap27:amd64 as Depends of libgdal28:amd64
            MarkInstall libdap27:amd64 < none -> 3.20.7-6 @un uN > FU=0
          Installing libdeflate0:amd64 as Depends of libgdal28:amd64
            MarkInstall libdeflate0:amd64 < none -> 1.7-1ubuntu1 @un uN > FU=0
          Installing libpoppler107:amd64 as Depends of libgdal28:amd64
            MarkInstall libpoppler107:amd64 < none -> 21.02.0-1 @un uN > FU=0
    Installing libopenvdb7.1:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libopenvdb7.1:amd64 < none -> 7.1.0-2build3 @un uN Ib > FU=0
      Installing libboost-iostreams1.74.0:amd64 as Depends of libopenvdb7.1:amd64
        MarkInstall libboost-iostreams1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN > FU=0
      Installing liblog4cplus-2.0.5:amd64 as Depends of libopenvdb7.1:amd64
        MarkInstall liblog4cplus-2.0.5:amd64 < none -> 2.0.5-3 @un uN > FU=0
    Installing libraw20:amd64 as Depends of libopenimageio2.2:amd64
      MarkInstall libraw20:amd64 < none -> 0.20.2-1ubuntu2 @un uN > FU=0
  Installing libpython3.9:amd64 as Depends of blender:amd64
    MarkInstall libpython3.9:amd64 < none -> 3.9.5-3~21.04 @un uN Ib > FU=0
    Installing libpython3.9-stdlib:amd64 as Depends of libpython3.9:amd64
      MarkInstall libpython3.9-stdlib:amd64 < none -> 3.9.5-3~21.04 @un uN Ib > FU=0
      Installing libpython3.9-minimal:amd64 as Depends of libpython3.9-stdlib:amd64
        MarkInstall libpython3.9-minimal:amd64 < none -> 3.9.5-3~21.04 @un uN > FU=0
      Installing libmpdec3:amd64 as Depends of libpython3.9-stdlib:amd64
        MarkInstall libmpdec3:amd64 < none -> 2.5.1-2 @un uN > FU=0
  MarkInstall python3-dev:amd64 < 3.8.6-0ubuntu1 -> 3.9.4-1 @ii umU Ib > FU=0
  Installing python3.9-dev:amd64 as Depends of python3-dev:amd64
    MarkInstall python3.9-dev:amd64 < none -> 3.9.5-3~21.04 @un uN Ib > FU=0
    Installing python3.9:amd64 as Depends of python3.9-dev:amd64
      MarkInstall python3.9:amd64 < none -> 3.9.5-3~21.04 @un uN Ib > FU=0
      Installing python3.9-minimal:amd64 as Depends of python3.9:amd64
        MarkInstall python3.9-minimal:amd64 < none -> 3.9.5-3~21.04 @un uN > FU=0
    Installing libpython3.9-dev:amd64 as Depends of python3.9-dev:amd64
      MarkInstall libpython3.9-dev:amd64 < none -> 3.9.5-3~21.04 @un uN > FU=0
  MarkInstall liblibreoffice-java:amd64 < 1:7.0.6-0ubuntu0.20.10.1 -> 1:7.1.6-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Installing ure-java:amd64 as Depends of liblibreoffice-java:amd64
    MarkInstall ure-java:amd64 < none -> 1:7.1.6-0ubuntu0.21.04.1 @un uN > FU=0
  MarkInstall libavformat58:amd64 < 7:4.3.1-4ubuntu1 -> 7:4.3.2-0+deb11u1ubuntu1 @ii umU Ib > FU=0
  Installing libsrt1.4-gnutls:amd64 as Depends of libavformat58:amd64
     Delayed Removing: libsrt1-gnutls:amd64 as upgrade is not an option for libsrt1.4-gnutls:amd64 (1.4.2-1.3)
    MarkInstall libsrt1.4-gnutls:amd64 < none -> 1.4.2-1.3 @un uN Ib > FU=0
    MarkDelete libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK > FU=0
  MarkInstall rpm2cpio:amd64 < 4.14.2.1+dfsg1-1.1 -> 4.16.1.2+dfsg1-0.6ubuntu2 @ii umU Ib > FU=0
  Installing librpm9:amd64 as Depends of rpm2cpio:amd64
    MarkInstall librpm9:amd64 < none -> 4.16.1.2+dfsg1-0.6ubuntu2 @un uN Ib > FU=0
    Installing librpmio9:amd64 as Depends of librpm9:amd64
      MarkInstall librpmio9:amd64 < none -> 4.16.1.2+dfsg1-0.6ubuntu2 @un uN > FU=0
  MarkInstall kdeconnect:amd64 < 20.08.2-0ubuntu1 -> 20.12.3-1 @ii umU Ib > FU=0
  Installing qml-module-qt-labs-platform:amd64 as Depends of kdeconnect:amd64
    MarkInstall qml-module-qt-labs-platform:amd64 < none -> 5.15.2+dfsg-2 @un uN > FU=0
  Installing qml-module-qtmultimedia:amd64 as Depends of kdeconnect:amd64
    MarkInstall qml-module-qtmultimedia:amd64 < none -> 5.15.2-3 @un uN Ib > FU=0
    Installing libqt5multimediaquick5:amd64 as Depends of qml-module-qtmultimedia:amd64
      MarkInstall libqt5multimediaquick5:amd64 < none -> 5.15.2-3 @un uN > FU=0
  MarkInstall linux-headers-generic:amd64 < 5.8.0.63.69 -> 5.11.0.38.39 @ii umU Ib > FU=0
  Installing linux-headers-5.11.0-38-generic:amd64 as Depends of linux-headers-generic:amd64
    MarkInstall linux-headers-5.11.0-38-generic:amd64 < none -> 5.11.0-38.42 @un uN Ib > FU=0
    Installing linux-headers-5.11.0-38:amd64 as Depends of linux-headers-5.11.0-38-generic:amd64
      MarkInstall linux-headers-5.11.0-38:amd64 < none -> 5.11.0-38.42 @un uN > FU=0
  MarkInstall gnome-control-center:amd64 < 1:3.38.3-0ubuntu1 -> 1:3.38.5-1ubuntu2 @ii umU IPb > FU=0
  new important dependency: power-profiles-daemon:amd64
  Installing power-profiles-daemon:amd64 as Recommends of gnome-control-center:amd64
    MarkInstall power-profiles-daemon:amd64 < none -> 0.1-5 @un uN > FU=0
  MarkInstall node-jquery:amd64 < 3.5.1+dfsg-4 -> 3.5.1+dfsg+~3.5.5-7 @ii umU IPb > FU=0
  new important dependency: libjs-sizzle:amd64
  Installing libjs-sizzle:amd64 as Recommends of node-jquery:amd64
    MarkInstall libjs-sizzle:amd64 < none -> 2.3.5+ds-2 @un uN > FU=0
  MarkInstall liblist-moreutils-perl:amd64 < 0.416-1build5 -> 0.430-2 @ii umU Ib > FU=0
  Installing liblist-moreutils-xs-perl:amd64 as Depends of liblist-moreutils-perl:amd64
    MarkInstall liblist-moreutils-xs-perl:amd64 < none -> 0.430-2 @un uN > FU=0
  MarkInstall g++-10:amd64 < 10.3.0-1ubuntu1~20.10 -> 10.3.0-1ubuntu1 @ii umU Ib > FU=0
  Installing libisl23:amd64 as Depends of g++-10:amd64
    MarkInstall libisl23:amd64 < none -> 0.23-1build1 @un uN > FU=0
  MarkInstall libpam-modules:amd64 < 1.3.1-5ubuntu6.20.10.1 -> 1.3.1-5ubuntu6.21.04.1 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on update-motd:amd64
  MarkInstall libjsoncpp-dev:amd64 < 1.7.4-3.1ubuntu2 -> 1.9.4-4 @ii umU Ib > FU=0
  Installing libjsoncpp24:amd64 as Depends of libjsoncpp-dev:amd64
    MarkInstall libjsoncpp24:amd64 < none -> 1.9.4-4 @un uN > FU=0
  MarkInstall libgphoto2-6:i386 < 2.5.25-3 -> 2.5.26-2 @ii umU Ib > FU=0
  Installing libcurl4:i386 as Depends of libgphoto2-6:i386
    MarkInstall libcurl4:i386 < none -> 7.74.0-1ubuntu2.3 @un uN > FU=0
  MarkInstall ubuntu-restricted-addons:amd64 < 26 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on gstreamer1.0-fluendo-mp3:amd64
  MarkInstall libgdk-pixbuf2.0-0:amd64 < 2.40.0+dfsg-5ubuntu0.2 -> 2.40.2-2build2 @ii umU Ib > FU=0
  Installing libgdk-pixbuf-xlib-2.0-0:amd64 as Depends of libgdk-pixbuf2.0-0:amd64
    MarkInstall libgdk-pixbuf-xlib-2.0-0:amd64 < none -> 2.40.2-2build2 @un uN > FU=0
  MarkInstall libgdk-pixbuf2.0-0:i386 < 2.40.0+dfsg-5ubuntu0.2 -> 2.40.2-2build2 @ii umU Ib > FU=0
  Installing libgdk-pixbuf-2.0-0:i386 as Depends of libgdk-pixbuf2.0-0:i386
    MarkInstall libgdk-pixbuf-2.0-0:i386 < none -> 2.42.2+dfsg-1build1 @un uN > FU=0
  Installing libgdk-pixbuf-xlib-2.0-0:i386 as Depends of libgdk-pixbuf2.0-0:i386
    MarkInstall libgdk-pixbuf-xlib-2.0-0:i386 < none -> 2.40.2-2build2 @un uN > FU=0
  MarkInstall xfce4-panel-profiles:amd64 < 1.0.10-0ubuntu1 -> 1.0.13-0ubuntu2 @ii umU Ib > FU=0
  Installing gir1.2-libxfce4ui-2.0:amd64 as Depends of xfce4-panel-profiles:amd64
    MarkInstall gir1.2-libxfce4ui-2.0:amd64 < none -> 4.16.0-1 @un uN Ib > FU=0
    Installing gir1.2-libxfce4util-1.0:amd64 as Depends of gir1.2-libxfce4ui-2.0:amd64
      MarkInstall gir1.2-libxfce4util-1.0:amd64 < none -> 4.16.0-1 @un uN > FU=0
  MarkInstall libgeos-c1v5:amd64 < 3.8.1-1 -> 3.9.0-1 @ii umU Ib > FU=0
  Installing libgeos-3.9.0:amd64 as Depends of libgeos-c1v5:amd64
    MarkInstall libgeos-3.9.0:amd64 < none -> 3.9.0-1 @un uN > FU=0
  MarkInstall linux-image-generic:amd64 < 5.8.0.63.69 -> 5.11.0.38.39 @ii umU Ib > FU=0
  Installing linux-image-5.11.0-38-generic:amd64 as Depends of linux-image-generic:amd64
    MarkInstall linux-image-5.11.0-38-generic:amd64 < none -> 5.11.0-38.42 @un uN Ib > FU=0
    Installing linux-modules-5.11.0-38-generic:amd64 as Depends of linux-image-5.11.0-38-generic:amd64
      MarkInstall linux-modules-5.11.0-38-generic:amd64 < none -> 5.11.0-38.42 @un uN > FU=0
  Installing linux-modules-extra-5.11.0-38-generic:amd64 as Depends of linux-image-generic:amd64
    MarkInstall linux-modules-extra-5.11.0-38-generic:amd64 < none -> 5.11.0-38.42 @un uN > FU=0
  MarkInstall libzmq5:amd64 < 4.3.2-2ubuntu2 -> 4.3.4-1 @ii umU Ib > FU=0
  Installing libpgm-5.3-0:amd64 as Depends of libzmq5:amd64
    MarkInstall libpgm-5.3-0:amd64 < none -> 5.3.128~dfsg-2 @un uN > FU=0
  MarkInstall libreoffice-core:amd64 < 1:7.0.6-0ubuntu0.20.10.1 -> 1:7.1.6-0ubuntu0.21.04.1 @ii umU Ib > FU=0
  Installing liborcus-0.16-0:amd64 as Depends of libreoffice-core:amd64
    MarkInstall liborcus-0.16-0:amd64 < none -> 0.16.1-3build2 @un uN Ib > FU=0
    Installing liborcus-parser-0.16-0:amd64 as Depends of liborcus-0.16-0:amd64
      MarkInstall liborcus-parser-0.16-0:amd64 < none -> 0.16.1-3build2 @un uN > FU=0
  MarkInstall libedata-cal-2.0-1:amd64 < 3.38.1-1 -> 3.40.0-1ubuntu1.1 @ii umU Ib > FU=0
  Installing libedataserver-1.2-26:amd64 as Depends of libedata-cal-2.0-1:amd64
    MarkInstall libedataserver-1.2-26:amd64 < none -> 3.40.0-1ubuntu1.1 @un uN > FU=0
  MarkInstall libmu-dbm6:amd64 < 1:3.9-3.2 @ii mK Ib > FU=0
    libmu-dbm6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2) can't be satisfied! (dep)
  MarkInstall lib32gcc-s1:amd64 < 10.3.0-1ubuntu1~20.10 -> 11.1.0-1ubuntu1~21.04 @ii umU Ib > FU=0
  Installing gcc-11-base:amd64 as Depends of lib32gcc-s1:amd64
    MarkInstall gcc-11-base:amd64 < none -> 11.1.0-1ubuntu1~21.04 @un uN > FU=0
  MarkInstall libopenmpi3:amd64 < 4.0.3-6ubuntu2 -> 4.1.0-7ubuntu2 @ii umU Ib > FU=0
  Installing libucx0:amd64 as Depends of libopenmpi3:amd64
    MarkInstall libucx0:amd64 < none -> 1.10.0~rc1-7 @un uN > FU=0
  MarkInstall libbsd0:amd64 < 0.10.0-1 -> 0.11.3-1ubuntu2 @ii umU Ib > FU=0
  Installing libmd0:amd64 as Depends of libbsd0:amd64
    MarkInstall libmd0:amd64 < none -> 1.0.3-3build1 @un uN > FU=0
  MarkInstall libbsd0:i386 < 0.10.0-1 -> 0.11.3-1ubuntu2 @ii umU Ib > FU=0
  Installing libmd0:i386 as Depends of libbsd0:i386
    MarkInstall libmd0:i386 < none -> 1.0.3-3build1 @un uN > FU=0
  MarkInstall xfce4-indicator-plugin:amd64 < 2.3.4-0ubuntu2 -> 2.4.0-1 @ii umU IPb > FU=0
  new important dependency: ayatana-indicator-application:amd64
  Installing ayatana-indicator-application:amd64 as Recommends of xfce4-indicator-plugin:amd64
    MarkInstall ayatana-indicator-application:amd64 < none -> 0.8.0-1 @un uN Ib > FU=0
    Installing ayatana-indicator-common:amd64 as Depends of ayatana-indicator-application:amd64
      MarkInstall ayatana-indicator-common:amd64 < none -> 0.8.4-1 @un uN > FU=0
  MarkInstall e2fsprogs:amd64 < 1.45.6-1ubuntu1 -> 1.45.7-1ubuntu2 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on e2fsprogs-l10n:amd64
  MarkInstall python3-pyqt5.qtwebengine:amd64 < 5.15.0-1 -> 5.15.4-1 @ii umU Ib > FU=0
  Installing python3-pyqt5.sip:amd64 as Depends of python3-pyqt5.qtwebengine:amd64
    MarkInstall python3-pyqt5.sip:amd64 < none -> 12.8.1-1build1 @un uN > FU=0
  MarkInstall pidgin:amd64 < 1:2.13.0-2.2ubuntu4 -> 1:2.14.1-1ubuntu1 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on pidgin-libnotify:amd64
  MarkInstall libfcgi-perl:amd64 < 0.79-1 -> 0.79+ds-2 @ii umU Ib > FU=0
  Installing libfcgi0ldbl:amd64 as Depends of libfcgi-perl:amd64
    MarkInstall libfcgi0ldbl:amd64 < none -> 2.4.2-2 @un uN IPb > FU=0
    Installing libfcgi-bin:amd64 as Recommends of libfcgi0ldbl:amd64
      MarkInstall libfcgi-bin:amd64 < none -> 2.4.2-2 @un uN > FU=0
  MarkInstall ubuntu-standard:amd64 < 1.459 -> 1.469 @ii umU Ib > FU=0
  Installing media-types:amd64 as Depends of ubuntu-standard:amd64
    MarkInstall media-types:amd64 < none -> 4.0.0 @un uN > FU=0
  MarkInstall supertuxkart-data:amd64 < 1.1+ds-1build2 -> 1.2+ds-2 @ii umU Ib > FU=0
  Installing fonts-noto-extra:amd64 as Depends of supertuxkart-data:amd64
    MarkInstall fonts-noto-extra:amd64 < none -> 20201225-1build1 @un uN > FU=0
  Installing fonts-noto-ui-extra:amd64 as Depends of supertuxkart-data:amd64
    MarkInstall fonts-noto-ui-extra:amd64 < none -> 20201225-1build1 @un uN > FU=0
  MarkInstall xfce4-settings:amd64 < 4.14.3-0ubuntu1 -> 4.16.0-1ubuntu1 @ii umU Ib > FU=0
  Installing xfce4-helpers:amd64 as Depends of xfce4-settings:amd64
     Delayed Removing: libexo-helpers:amd64 as upgrade is not an option for xfce4-helpers:amd64 (4.16.0-1ubuntu1)
    MarkInstall xfce4-helpers:amd64 < none -> 4.16.0-1ubuntu1 @un uN Ib > FU=0
    MarkDelete libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK > FU=0
  MarkInstall gdb:amd64 < 9.2-0ubuntu2 -> 10.1-2ubuntu2 @ii umU Ib > FU=0
  Installing libdebuginfod1:amd64 as Depends of gdb:amd64
    MarkInstall libdebuginfod1:amd64 < none -> 0.183-8 @un uN Ib > FU=0
    Installing libdebuginfod-common:amd64 as Depends of libdebuginfod1:amd64
      MarkInstall libdebuginfod-common:amd64 < none -> 0.183-8 @un uN > FU=0
  Installing libipt2:amd64 as Depends of gdb:amd64
    MarkInstall libipt2:amd64 < none -> 2.0.3-1 @un uN > FU=0
  Installing libsource-highlight4v5:amd64 as Depends of gdb:amd64
    MarkInstall libsource-highlight4v5:amd64 < none -> 3.1.9-3build1 @un uN Ib > FU=0
    Installing libsource-highlight-common:amd64 as Depends of libsource-highlight4v5:amd64
      MarkInstall libsource-highlight-common:amd64 < none -> 3.1.9-3build1 @un uN > FU=0
    Installing libboost-regex1.74.0:amd64 as Depends of libsource-highlight4v5:amd64
      MarkInstall libboost-regex1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN > FU=0
  MarkInstall libxatracker2:amd64 < 20.2.6-0ubuntu0.20.10.1 -> 21.0.3-0ubuntu0.3 @ii umU Ib > FU=0
  Installing libllvm12:amd64 as Depends of libxatracker2:amd64
    MarkInstall libllvm12:amd64 < none -> 1:12.0.0-3ubuntu1~21.04.2 @un uN > FU=0
  MarkInstall libexo-1-0:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK Ib > FU=0
  Installing libexo-helpers:amd64 as Depends of libexo-1-0:amd64
      MarkKeep libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mR > FU=0
  MarkInstall xbrlapi:amd64 < 6.0+dfsg-4ubuntu7 -> 6.3+dfsg-1ubuntu1 @ii umU Ib > FU=0
  Installing libbrlapi0.8:amd64 as Depends of xbrlapi:amd64
    MarkInstall libbrlapi0.8:amd64 < none -> 6.3+dfsg-1ubuntu1 @un uN > FU=0
  MarkInstall mime-support:amd64 < 3.64ubuntu1 -> 3.66 @ii umU Ib > FU=0
  Installing mailcap:amd64 as Depends of mime-support:amd64
    MarkInstall mailcap:amd64 < none -> 3.68ubuntu1 @un uN > FU=0
  MarkInstall evolution-data-server:amd64 < 3.38.1-1 -> 3.40.0-1ubuntu1.1 @ii umU Ib > FU=0
  Installing libedataserverui-1.2-3:amd64 as Depends of evolution-data-server:amd64
    MarkInstall libedataserverui-1.2-3:amd64 < none -> 3.40.0-1ubuntu1.1 @un uN > FU=0
  MarkInstall python3-twisted:amd64 < 18.9.0-11ubuntu0.20.10.1 -> 20.3.0-4ubuntu1 @ii umU Ib > FU=0
  Installing python3-bcrypt:amd64 as Depends of python3-twisted:amd64
    MarkInstall python3-bcrypt:amd64 < none -> 3.1.7-4 @un uN > FU=0
  MarkInstall python3-opencv:amd64 < 4.2.0+dfsg-6build6 -> 4.5.1+dfsg-4ubuntu1 @ii umU Ib > FU=0
  Installing libopencv-calib3d4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-calib3d4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
    Installing libopencv-features2d4.5:amd64 as Depends of libopencv-calib3d4.5:amd64
      MarkInstall libopencv-features2d4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
      Installing libopencv-flann4.5:amd64 as Depends of libopencv-features2d4.5:amd64
        MarkInstall libopencv-flann4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
      Installing libopencv-highgui4.5:amd64 as Depends of libopencv-features2d4.5:amd64
        MarkInstall libopencv-highgui4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
      Installing libopencv-ml4.5:amd64 as Depends of libopencv-features2d4.5:amd64
        MarkInstall libopencv-ml4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-dnn4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-dnn4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-objdetect4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-objdetect4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-photo4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-photo4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-shape4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-shape4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
    Installing libopencv-video4.5:amd64 as Depends of libopencv-shape4.5:amd64
      MarkInstall libopencv-video4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-stitching4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-stitching4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
  Installing libopencv-superres4.5:amd64 as Depends of python3-opencv:amd64
    MarkInstall libopencv-superres4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
    Installing libopencv-contrib4.5:amd64 as Depends of libopencv-superres4.5:amd64
      MarkInstall libopencv-contrib4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
      Installing libopencv-videostab4.5:amd64 as Depends of libopencv-contrib4.5:amd64
        MarkInstall libopencv-videostab4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN > FU=0
      Installing libopencv-viz4.5:amd64 as Depends of libopencv-contrib4.5:amd64
        MarkInstall libopencv-viz4.5:amd64 < none -> 4.5.1+dfsg-4ubuntu1 @un uN Ib > FU=0
        Installing libvtk9:amd64 as Depends of libopencv-viz4.5:amd64
          MarkInstall libvtk9:amd64 < none -> 9.0.1+dfsg1-8 @un uN > FU=0
  MarkInstall ubuntu-minimal:amd64 < 1.459 -> 1.469 @ii umU IPb > FU=0
  new important dependency: usrmerge:amd64
  Installing usrmerge:amd64 as Recommends of ubuntu-minimal:amd64
    MarkInstall usrmerge:amd64 < none -> 24ubuntu3 @un uN > FU=0
  MarkInstall gimp:amd64 < 2.10.18-1build2 -> 2.10.22-3 @ii umU Ib > FU=0
  Installing graphviz:amd64 as Depends of gimp:amd64
    MarkInstall graphviz:amd64 < none -> 2.42.2-4build2 @un uN Ib > FU=0
    Installing libann0:amd64 as Depends of graphviz:amd64
      MarkInstall libann0:amd64 < none -> 1.1.2+doc-7build1 @un uN > FU=0
    Installing libcdt5:amd64 as Depends of graphviz:amd64
      MarkInstall libcdt5:amd64 < none -> 2.42.2-4build2 @un uN > FU=0
    Installing libcgraph6:amd64 as Depends of graphviz:amd64
      MarkInstall libcgraph6:amd64 < none -> 2.42.2-4build2 @un uN > FU=0
    Installing libgts-0.7-5:amd64 as Depends of graphviz:amd64
      MarkInstall libgts-0.7-5:amd64 < none -> 0.7.6+darcs121130-4 @un uN IPb > FU=0
      Installing libgts-bin:amd64 as Recommends of libgts-0.7-5:amd64
        MarkInstall libgts-bin:amd64 < none -> 0.7.6+darcs121130-4 @un uN > FU=0
    Installing libgvc6:amd64 as Depends of graphviz:amd64
      MarkInstall libgvc6:amd64 < none -> 2.42.2-4build2 @un uN Ib > FU=0
      Installing libpathplan4:amd64 as Depends of libgvc6:amd64
        MarkInstall libpathplan4:amd64 < none -> 2.42.2-4build2 @un uN > FU=0
    Installing libgvpr2:amd64 as Depends of graphviz:amd64
      MarkInstall libgvpr2:amd64 < none -> 2.42.2-4build2 @un uN > FU=0
    Installing liblab-gamut1:amd64 as Depends of graphviz:amd64
      MarkInstall liblab-gamut1:amd64 < none -> 2.42.2-4build2 @un uN > FU=0
  MarkInstall libboost-dev:amd64 < 1.71.0.0ubuntu4 -> 1.74.0.3ubuntu5 @ii umU Ib > FU=0
  Installing libboost1.74-dev:amd64 as Depends of libboost-dev:amd64
    MarkKeep libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU > FU=0
     Delayed Removing: libboost1.71-dev:amd64 as upgrade is not an option for libboost1.74-dev:amd64 (1.74.0-8ubuntu2)
    MarkInstall libboost1.74-dev:amd64 < none -> 1.74.0-8ubuntu2 @un uN Ib > FU=0
    MarkDelete libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 | 1.71.0-6ubuntu11 @ii umH > FU=0
  MarkInstall libsane1:amd64 < 1.0.31-2ubuntu0.20.10 -> 1.0.32-0ubuntu2 @ii umU Ib > FU=0
  Installing libsnmp40:amd64 as Depends of libsane1:amd64
    MarkInstall libsnmp40:amd64 < none -> 5.9+dfsg-3ubuntu1.21.04.1 @un uN Ib > FU=0
    Installing libperl5.32:amd64 as Depends of libsnmp40:amd64
      MarkInstall libperl5.32:amd64 < none -> 5.32.1-3ubuntu2.1 @un uN Ib > FU=0
      Installing perl-modules-5.32:amd64 as Depends of libperl5.32:amd64
        MarkInstall perl-modules-5.32:amd64 < none -> 5.32.1-3ubuntu2.1 @un uN > FU=0
  new important dependency: sane-airscan:amd64
  Installing sane-airscan:amd64 as Recommends of libsane1:amd64
    MarkInstall sane-airscan:amd64 < none -> 0.99.25-0ubuntu1 @un uN > FU=0
  MarkInstall libsane1:i386 < 1.0.31-2ubuntu0.20.10 -> 1.0.32-0ubuntu2 @ii umU NPb Ib > FU=0
  Installing libsnmp40:i386 as Depends of libsane1:i386
    MarkInstall libsnmp40:i386 < none -> 5.9+dfsg-3ubuntu1.21.04.1 @un uN Ib > FU=0
    Installing libperl5.32:i386 as Depends of libsnmp40:i386
      MarkInstall libperl5.32:i386 < none -> 5.32.1-3ubuntu2.1 @un uN > FU=0
  new important dependency: sane-airscan:i386
    libsane1:i386 Recommends on sane-airscan:i386 < none @un H > can't be satisfied! (dep)
  MarkInstall libtiff5:i386 < 4.1.0+git191117-2ubuntu0.20.10.1 -> 4.2.0-1build1 @ii umU Ib > FU=0
  Installing libdeflate0:i386 as Depends of libtiff5:i386
    MarkInstall libdeflate0:i386 < none -> 1.7-1ubuntu1 @un uN > FU=0
  MarkInstall libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU > FU=0
  MarkInstall libgnome-desktop-3-19:amd64 < 3.38.3-0ubuntu1 -> 3.38.5-1ubuntu2~21.04.2 @ii umU Ib > FU=0
  Installing libxkbregistry0:amd64 as Depends of libgnome-desktop-3-19:amd64
    MarkInstall libxkbregistry0:amd64 < none -> 1.0.3-2 @un uN > FU=0
  MarkInstall libgsasl7:amd64 < 1.8.1-1 -> 1.10.0-4 @ii umU Ib > FU=0
  Installing gsasl-common:amd64 as Depends of libgsasl7:amd64
    MarkInstall gsasl-common:amd64 < none -> 1.10.0-4 @un uN > FU=0
  MarkInstall rpm:amd64 < 4.14.2.1+dfsg1-1.1 -> 4.16.1.2+dfsg1-0.6ubuntu2 @ii umU Ib > FU=0
  Installing librpmbuild9:amd64 as Depends of rpm:amd64
    MarkInstall librpmbuild9:amd64 < none -> 4.16.1.2+dfsg1-0.6ubuntu2 @un uN > FU=0
  Installing librpmsign9:amd64 as Depends of rpm:amd64
    MarkInstall librpmsign9:amd64 < none -> 4.16.1.2+dfsg1-0.6ubuntu2 @un uN > FU=0
  MarkInstall ruby:amd64 < 1:2.7+1 -> 1:2.7+2 @ii umU Ib > FU=0
  Installing ruby-rubygems:amd64 as Depends of ruby:amd64
    MarkInstall ruby-rubygems:amd64 < none -> 3.2.5-2 @un uN > FU=0
  MarkInstall librpm8:amd64 < 4.14.2.1+dfsg1-1.1 @ii mK IPb > FU=0
  previously satisfied important dependency on rpm-common:amd64
    librpm8:amd64 Recommends on rpm-common:amd64 < 4.14.2.1+dfsg1-1.1 -> 4.16.1.2+dfsg1-0.6ubuntu2 @ii umU > (= 4.14.2.1+dfsg1-1.1) can't be satisfied! (dep)
  MarkInstall libepub0:amd64 < 0.2.2-4ubuntu2 -> 0.2.2-4ubuntu3 @ii umU Ib > FU=0
  Installing libzip4:amd64 as Depends of libepub0:amd64
    MarkInstall libzip4:amd64 < none -> 1.7.3-1ubuntu1 @un uN > FU=0
  MarkInstall mailutils:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU Ib > FU=0
  Installing libmailutils8:amd64 as Depends of mailutils:amd64
    MarkInstall libmailutils8:amd64 < none -> 1:3.11.1-5 @un uN Ib > FU=0
    Installing guile-3.0-libs:amd64 as Depends of libmailutils8:amd64
      MarkInstall guile-3.0-libs:amd64 < none -> 3.0.5-2 @un uN > FU=0
  MarkInstall acpi-support:amd64 < 0.143 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on toshset:amd64
  MarkInstall lintian:amd64 < 2.89.0ubuntu1 -> 2.104.0ubuntu2 @ii umU Ib > FU=0
  Installing libhtml-html5-entities-perl:amd64 as Depends of lintian:amd64
    MarkInstall libhtml-html5-entities-perl:amd64 < none -> 0.004-1.1 @un uN > FU=0
  Installing libproc-processtable-perl:amd64 as Depends of lintian:amd64
    MarkInstall libproc-processtable-perl:amd64 < none -> 0.59-2build1 @un uN > FU=0
  Installing libtext-markdown-discount-perl:amd64 as Depends of lintian:amd64
    MarkInstall libtext-markdown-discount-perl:amd64 < none -> 0.12-1build1 @un uN Ib > FU=0
    Installing libmarkdown2:amd64 as Depends of libtext-markdown-discount-perl:amd64
      MarkInstall libmarkdown2:amd64 < none -> 2.2.6-1ubuntu1 @un uN > FU=0
  MarkInstall libgomp1:i386 < 10.3.0-1ubuntu1~20.10 -> 11.1.0-1ubuntu1~21.04 @ii umU Ib > FU=0
  Installing gcc-11-base:i386 as Depends of libgomp1:i386
    MarkInstall gcc-11-base:i386 < none -> 11.1.0-1ubuntu1~21.04 @un uN > FU=0
  MarkInstall iproute2:amd64 < 5.7.0-1ubuntu1 -> 5.10.0-4ubuntu1 @ii umU Ib > FU=0
  Installing libbpf0:amd64 as Depends of iproute2:amd64
    MarkInstall libbpf0:amd64 < none -> 1:0.3-2ubuntu1 @un uN > FU=0
  MarkInstall libgl1-mesa-dri:i386 < 20.2.6-0ubuntu0.20.10.1 -> 21.0.3-0ubuntu0.3 @ii umU Ib > FU=0
  Installing libllvm12:i386 as Depends of libgl1-mesa-dri:i386
    MarkInstall libllvm12:i386 < none -> 1:12.0.0-3ubuntu1~21.04.2 @un uN > FU=0
  MarkInstall libwine-development:amd64 < 5.5-5ubuntu1 -> 5.6-2 @ii umU Ib > FU=0
  Installing libz-mingw-w64:amd64 as Depends of libwine-development:amd64
    MarkInstall libz-mingw-w64:amd64 < none -> 1.2.11+dfsg-2 @un uN > FU=0
  MarkInstall catfish:amd64 < 1.4.13-1 -> 4.16.0-1 @ii umU Ib > FU=0
  Installing gir1.2-xfconf-0:amd64 as Depends of catfish:amd64
    MarkInstall gir1.2-xfconf-0:amd64 < none -> 4.16.0-2 @un uN > FU=0
  MarkInstall libmailutils6:amd64 < 1:3.9-3.2 @ii mK Ib > FU=0
    libmailutils6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2) can't be satisfied! (dep)
  MarkInstall libc-dev-bin:amd64 < 2.32-0ubuntu3 -> 2.33-0ubuntu5 @ii umU IPb > FU=0
  new important dependency: libc-devtools:amd64
  Installing libc-devtools:amd64 as Recommends of libc-dev-bin:amd64
    MarkInstall libc-devtools:amd64 < none -> 2.33-0ubuntu5 @un uN > FU=0
  MarkInstall audacious-plugins:amd64 < 4.0.4-1build1 -> 4.0.5-1 @ii umU Ib > FU=0
  Installing libsidplayfp5:amd64 as Depends of audacious-plugins:amd64
     Delayed Removing: libsidplayfp4:amd64 as upgrade is not an option for libsidplayfp5:amd64 (2.0.5-2)
    MarkInstall libsidplayfp5:amd64 < none -> 2.0.5-2 @un uN Ib > FU=0
    MarkDelete libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK > FU=0
  MarkInstall fwupd:amd64 < 1.4.7-0~20.10.2 -> 1.5.11-0ubuntu1~21.04.1 @ii umU Ib > FU=0
  Installing libtss2-esys-3.0.2-0:amd64 as Depends of fwupd:amd64
     Delayed Removing: libtss2-esys0:amd64 as upgrade is not an option for libtss2-esys-3.0.2-0:amd64 (3.0.3-2ubuntu1)
    MarkInstall libtss2-esys-3.0.2-0:amd64 < none -> 3.0.3-2ubuntu1 @un uN Ib > FU=0
    Installing libtss2-tcti-cmd0:amd64 as Depends of libtss2-esys-3.0.2-0:amd64
       Delayed Removing: libtss2-esys0:amd64 as upgrade is not an option for libtss2-tcti-cmd0:amd64 (3.0.3-2ubuntu1)
      MarkInstall libtss2-tcti-cmd0:amd64 < none -> 3.0.3-2ubuntu1 @un uN Ib > FU=0
      Installing libtss2-mu0:amd64 as Depends of libtss2-tcti-cmd0:amd64
         Delayed Removing: libtss2-esys0:amd64 as upgrade is not an option for libtss2-mu0:amd64 (3.0.3-2ubuntu1)
        MarkInstall libtss2-mu0:amd64 < none -> 3.0.3-2ubuntu1 @un uN Ib > FU=0
        MarkDelete libtss2-esys0:amd64 < 3.0.1-1 @ii mK > FU=0
    Installing libtss2-tcti-device0:amd64 as Depends of libtss2-esys-3.0.2-0:amd64
      MarkInstall libtss2-tcti-device0:amd64 < none -> 3.0.3-2ubuntu1 @un uN > FU=0
    Installing libtss2-tcti-mssim0:amd64 as Depends of libtss2-esys-3.0.2-0:amd64
      MarkInstall libtss2-tcti-mssim0:amd64 < none -> 3.0.3-2ubuntu1 @un uN > FU=0
    Installing libtss2-tcti-swtpm0:amd64 as Depends of libtss2-esys-3.0.2-0:amd64
      MarkInstall libtss2-tcti-swtpm0:amd64 < none -> 3.0.3-2ubuntu1 @un uN > FU=0
    Installing libtss2-sys1:amd64 as Depends of libtss2-esys-3.0.2-0:amd64
      MarkInstall libtss2-sys1:amd64 < none -> 3.0.3-2ubuntu1 @un uN > FU=0
  MarkInstall libqt5webenginecore5:amd64 < 5.14.2+dfsg1-5 -> 5.15.3+dfsg-5ubuntu1 @ii umU Ib > FU=0
  Installing libre2-9:amd64 as Depends of libqt5webenginecore5:amd64
    MarkInstall libre2-9:amd64 < none -> 20210201+dfsg-1 @un uN > FU=0
  MarkInstall libebook-contacts-1.2-3:amd64 < 3.38.1-1 -> 3.40.0-1ubuntu1.1 @ii umU Ib > FU=0
  Installing libphonenumber8:amd64 as Depends of libebook-contacts-1.2-3:amd64
    MarkInstall libphonenumber8:amd64 < none -> 8.12.16-4build1 @un uN > FU=0
  MarkInstall unity-settings-daemon:amd64 < 15.04.1+20.04.20200325-0ubuntu1 -> 15.04.1+20.04.20200325-0ubuntu2 @ii umU NPb IPb > FU=0
  ignore old unsatisfied important dependency on systemd-services:amd64
  MarkInstall calibre-bin:amd64 < 4.99.12+dfsg+really4.23.0-1 -> 5.11.0+dfsg-1 @ii umU Ib > FU=0
  Installing libpodofo0.9.7:amd64 as Depends of calibre-bin:amd64
    MarkInstall libpodofo0.9.7:amd64 < none -> 0.9.7+dfsg-2 @un uN > FU=0
  MarkInstall python3-libtorrent:amd64 < 1.2.5-1.2 -> 1.2.9-0.2fakesync1build1 @ii umU Ib > FU=0
  Installing libboost-python1.74.0:amd64 as Depends of python3-libtorrent:amd64
    MarkInstall libboost-python1.74.0:amd64 < none -> 1.74.0-8ubuntu2 @un uN > FU=0
  MarkInstall calibre:amd64 < 4.99.12+dfsg+really4.23.0-1 -> 5.11.0+dfsg-1 @ii umU Ib > FU=0
  Installing python3-py7zr:amd64 as Depends of calibre:amd64
    MarkInstall python3-py7zr:amd64 < none -> 0.11.3+dfsg-1 @un uN Ib > FU=0
    Installing python3-texttable:amd64 as Depends of python3-py7zr:amd64
      MarkInstall python3-texttable:amd64 < none -> 1.6.3-1 @un uN > FU=0
  Installing python3-speechd:amd64 as Depends of calibre:amd64
    MarkInstall python3-speechd:amd64 < none -> 0.10.2-2 @un uN > FU=0
  MarkInstall openshot-qt:amd64 < 2.5.1+dfsg1-1 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on inkscape:amd64
  MarkInstall xubuntu-desktop:amd64 < 2.233 -> 2.237 @ii umU IPb > FU=0
  new important dependency: adwaita-icon-theme-full:amd64
  Installing adwaita-icon-theme-full:amd64 as Recommends of xubuntu-desktop:amd64
    MarkInstall adwaita-icon-theme-full:amd64 < none -> 3.38.0-1ubuntu2 @un uN > FU=0
  new important dependency: hexchat:amd64
  Installing hexchat:amd64 as Recommends of xubuntu-desktop:amd64
    MarkInstall hexchat:amd64 < none -> 2.14.3-6~0ubuntu21.04.1 @un uN Ib > FU=0
    Installing hexchat-common:amd64 as Depends of hexchat:amd64
      MarkInstall hexchat-common:amd64 < none -> 2.14.3-6~0ubuntu21.04.1 @un uN > FU=0
    Installing hexchat-perl:amd64 as Recommends of hexchat:amd64
      MarkInstall hexchat-perl:amd64 < none -> 2.14.3-6~0ubuntu21.04.1 @un uN > FU=0
    Installing hexchat-plugins:amd64 as Recommends of hexchat:amd64
      MarkInstall hexchat-plugins:amd64 < none -> 2.14.3-6~0ubuntu21.04.1 @un uN > FU=0
    Installing hexchat-python3:amd64 as Recommends of hexchat:amd64
      MarkInstall hexchat-python3:amd64 < none -> 2.14.3-6~0ubuntu21.04.1 @un uN > FU=0
  MarkInstall libpoppler-glib8:i386 < 20.09.0-2ubuntu2 -> 21.02.0-1 @ii umU Ib > FU=0
  Installing libpoppler107:i386 as Depends of libpoppler-glib8:i386
    MarkInstall libpoppler107:i386 < none -> 21.02.0-1 @un uN > FU=0
  MarkInstall libmono-webbrowser4.0-cil:amd64 < 6.12.0.122-0xamarin1+ubuntu2004b1 @ii mK NPb IPb > FU=0
  ignore old unsatisfied important dependency on libgluezilla:amd64
    MarkKeep libsidplayfp4:amd64 < 1.8.8-1build1 @ii mR > FU=0
  MarkInstall libbluray2:amd64 < 1:1.2.0-3 -> 1:1.2.1-4 @ii umU Ib > FU=0
  Installing libudfread0:amd64 as Depends of libbluray2:amd64
    MarkInstall libudfread0:amd64 < none -> 1.1.1-1 @un uN > FU=0
  MarkInstall dpkg-dev:amd64 < 1.20.5ubuntu2 -> 1.20.9ubuntu1 @ii umU Ib > FU=0
  Installing lto-disabled-list:amd64 as Depends of dpkg-dev:amd64
    MarkInstall lto-disabled-list:amd64 < none -> 7 @un uN > FU=0
    MarkKeep libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mR > FU=0
    MarkKeep libtss2-esys0:amd64 < 3.0.1-1 @ii mR > FU=0
Starting pkgProblemResolver with broken count: 15
Starting 2 pkgProblemResolver with broken count: 15
Investigating (0) libsrt1.4-gnutls:amd64 < none -> 1.4.2-1.3 @un uN Ib >
Broken libsrt1.4-gnutls:amd64 Breaks on libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK >
  Considering libsrt1-gnutls:amd64 -3 as a solution to libsrt1.4-gnutls:amd64 21
  Added libsrt1-gnutls:amd64 to the remove list
  MarkDelete libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK > FU=0
  Fixing libsrt1.4-gnutls:amd64 via remove of libsrt1-gnutls:amd64
Investigating (0) libtss2-esys-3.0.2-0:amd64 < none -> 3.0.3-2ubuntu1 @un uN Ib >
Broken libtss2-esys-3.0.2-0:amd64 Breaks on libtss2-esys0:amd64 < 3.0.1-1 @ii mK > (< 3.0.2-1)
  Considering libtss2-esys0:amd64 -9 as a solution to libtss2-esys-3.0.2-0:amd64 5
  Added libtss2-esys0:amd64 to the remove list
  MarkDelete libtss2-esys0:amd64 < 3.0.1-1 @ii mK > FU=0
  Fixing libtss2-esys-3.0.2-0:amd64 via remove of libtss2-esys0:amd64
Investigating (0) xfce4-helpers:amd64 < none -> 4.16.0-1ubuntu1 @un uN Ib >
Broken xfce4-helpers:amd64 Breaks on libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK >
  Considering libexo-helpers:amd64 -2 as a solution to xfce4-helpers:amd64 3
  Added libexo-helpers:amd64 to the remove list
  MarkDelete libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK > FU=0
  Fixing xfce4-helpers:amd64 via remove of libexo-helpers:amd64
Investigating (0) python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
  Considering python-minimal:amd64 5096 as a solution to python2-minimal:amd64 1
  MarkKeep python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2-minimal:amd64 rather than change python-minimal:amd64
Investigating (0) libsidplayfp5:amd64 < none -> 2.0.5-2 @un uN Ib >
Broken libsidplayfp5:amd64 Breaks on libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK >
  Considering libsidplayfp4:amd64 -3 as a solution to libsidplayfp5:amd64 1
  Added libsidplayfp4:amd64 to the remove list
  MarkDelete libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK > FU=0
  Fixing libsidplayfp5:amd64 via remove of libsidplayfp4:amd64
Investigating (0) python2:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2:amd64 PreDepends on python2-minimal:amd64 < none | 2.7.18-2 @un umH > (= 2.7.18-2)
  Considering python2-minimal:amd64 1 as a solution to python2:amd64 1
  MarkKeep python2:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2:amd64 rather than change python2-minimal:amd64
Investigating (0) python-is-python2:amd64 < none -> 2.7.18-9 @un pumN Ib >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
  Considering python2:amd64 1 as a solution to python-is-python2:amd64 0
  Re-Instated python2-minimal:amd64
  Re-Instated python2:amd64
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Investigating (0) libboost1.74-dev:amd64 < none -> 1.74.0-8ubuntu2 @un uN Ib >
Broken libboost1.74-dev:amd64 Conflicts on libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU >
  Considering libboost1.71-dev:amd64 -1 as a solution to libboost1.74-dev:amd64 0
  Added libboost1.71-dev:amd64 to the remove list
  Conflicts//Breaks against version 1.71.0-6ubuntu9 for libboost1.71-dev but that is not InstVer, ignoring
  MarkDelete libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU > FU=0
  Fixing libboost1.74-dev:amd64 via remove of libboost1.71-dev:amd64
Investigating (0) libmailutils6:amd64 < 1:3.9-3.2 @ii mK Ib >
Broken libmailutils6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2)
  Considering mailutils-common:amd64 4 as a solution to libmailutils6:amd64 -1
  Removing libmailutils6:amd64 rather than change mailutils-common:amd64
  MarkDelete libmailutils6:amd64 < 1:3.9-3.2 @ii mK Ib > FU=0
Investigating (0) libmu-dbm6:amd64 < 1:3.9-3.2 @ii mK Ib >
Broken libmu-dbm6:amd64 Depends on mailutils-common:amd64 < 1:3.9-3.2 -> 1:3.11.1-5 @ii umU > (= 1:3.9-3.2)
  Considering mailutils-common:amd64 4 as a solution to libmu-dbm6:amd64 -1
  Removing libmu-dbm6:amd64 rather than change mailutils-common:amd64
  MarkDelete libmu-dbm6:amd64 < 1:3.9-3.2 @ii mK Ib > FU=0
Investigating (0) libexo-1-0:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK Ib >
Broken libexo-1-0:amd64 Depends on libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mR >
  Considering libexo-helpers:amd64 -2 as a solution to libexo-1-0:amd64 -2
  Removing libexo-1-0:amd64 rather than change libexo-helpers:amd64
  MarkDelete libexo-1-0:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK Ib > FU=0
Investigating (1) python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
  Considering python-minimal:amd64 5096 as a solution to python2-minimal:amd64 1
  MarkKeep python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2-minimal:amd64 rather than change python-minimal:amd64
Investigating (1) python2:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2:amd64 PreDepends on python2-minimal:amd64 < none | 2.7.18-2 @un umH > (= 2.7.18-2)
  Considering python2-minimal:amd64 1 as a solution to python2:amd64 0
  MarkKeep python2:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2:amd64 rather than change python2-minimal:amd64
Investigating (1) python-is-python2:amd64 < none -> 2.7.18-9 @un pumN Ib >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
  Considering python2:amd64 0 as a solution to python-is-python2:amd64 0
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Investigating (2) python-is-python2:amd64 < none -> 2.7.18-9 @un pumN Ib >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
  Considering python2:amd64 0 as a solution to python-is-python2:amd64 0
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Done
Log time: 2021-10-31 08:34:21.731489
```

---

### Post by MAFoElffen on 2021-10-31
If you change the quote tags in your last post to code tags, that would be a lot easier to read...

I copied it to a file and analyzed it in a code editor...

The problems seem to stem from trying to figure out how to get to python2:amd64 and pythin2-minimal:amd64 version equal to or newer than 2.7.18-9...

But you said you were on Release version 20.10 right? That IS the current version in 20.10, 21,04 and 21.10... Did you upgrade to current updates before you tried to do a do-release upgrade? If you did, then I'm at a loss, because that is already what should be there as those package versions already...

---

### Post by peyre on 2021-10-31
Oh yes!  Fixed it.

I didn't do anything proactive; I just let it update and upgrade when it asks to.  When the upgrades started failing, I kept applying updates when it asked.

---

### Post by MAFoElffen on 2021-10-31
> **peyre said:**
> When the upgrades started failing, I kept applying updates when it asked.

You mean about last August 2021 or so when the 20.10 mainline repo's went dark? Or do you mean your updates started failing in other ways a while ago? Please explain that.

Please do this (just to check what is there...)
```

suso apt-cache show python2-minimal
sudo apt-cache show python2

```
What is curious is that 21.04 is still live, for a few months... so it is not that it is trying to skip 'many' versions.... Which would be more complex.

---

### Post by peyre on 2021-10-31
I'm not sure just when it happened - didn't really start paying attention until the 21.04 upgrade failed.

Cool, let's see... the first returns:

```
Package: python2-minimal
Architecture: amd64
Version: 2.7.18-2
Multi-Arch: allowed
Priority: optional
Section: universe/python
Source: python-defaults
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 67
Depends: python2.7-minimal (>= 2.7.18~), dpkg (>= 1.13.20)
Recommends: python2
Conflicts: python-central (<< 0.5.5)
Breaks: idle (<< 2.6), python (<= 2.7.3-1~), python-all (<< 2.6), python-all-dbg (<< 2.6), python-all-dev (<< 2.6), python-dbg (<< 2.6), python-dev (<< 2.6), python-examples (<< 2.6), python-minimal (<< 2.7.15-2), python-support (<< 1.0.10ubuntu2), python2.5-minimal (<< 2.5.5-7), python2.6-minimal (<< 2.6.5~rc2-2), python3.1-minimal (<< 3.1.2~rc1-2)
Replaces: python (<= 2.7.3-1~), python-minimal (<< 2.7.15-2)
Filename: pool/universe/p/python-defaults/python2-minimal_2.7.18-2_amd64.deb
Size: 13480
MD5sum: 8c58d5834d23be96534d6766dfdd3c46
SHA1: 4963e27d2803f598d9dc13c91065ae9649fb9ee7
SHA256: becad3577bcc0655455f9260d48b6ca7dfdd310caf6c6224e8ca752199692a53
SHA512: 01b42ff56e0caac19a81772286564bcc1d132339ffe9546622fb47ffaecc46489addf3efa35bfefb1f2b64cc32e6eae1b717e7810022907828674851b47f5c8c
Homepage: https://www.python.org/
Description-en: minimal subset of the Python2 language
 This package contains the interpreter and some essential modules.  It's used
 in the boot process for some basic tasks.
 See /usr/share/doc/python2.7-minimal/README.Debian for a list of the modules
 contained in this package.
Description-md5: 39bbe74365740924be57582a5cfc507f
Cnf-Visible-Pkgname: python2
```

The second returns:

```
Package: python2
Architecture: amd64
Version: 2.7.18-2
Multi-Arch: allowed
Priority: optional
Section: universe/python
Source: python-defaults
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Matthias Klose <doko@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 69
Provides: python-ctypes, python-email, python-importlib, python-profiler, python-wsgiref
Pre-Depends: python2-minimal (= 2.7.18-2)
Depends: python2.7 (>= 2.7.18~), libpython2-stdlib (= 2.7.18-2)
Suggests: python2-doc (= 2.7.18-2), python-tk (>= 2.7.18~)
Conflicts: python-central (<< 0.5.5)
Breaks: python (<< 2.7.15-2), python2-doc (<< 2.7.18-2), update-manager-core (<< 0.200.5-2)
Replaces: python (<< 2.7.15-2), python-dev (<< 2.6.5-2), python2-doc (<< 2.7.18-2)
Filename: pool/universe/p/python-defaults/python2_2.7.18-2_amd64.deb
Size: 9068
MD5sum: 4e4b7a35f6dd90bb4d05755e716c17e7
SHA1: a54593c8ad3075ec697bd356464fd41c53a6deae
SHA256: d9dd4a2812a1cf7592dff0a6e939c9cddc57d9e361280f81e63149b44006340c
SHA512: 2046655a5f37163b2a578b193a907c2b017be996d8e776e3fc1b47f2ec8f191bb7e51b09e0579e10247c8271c5e0633351ebca90212ec5c79109a9ee0e32c41e
Homepage: https://www.python.org/
Description-en: interactive high-level object-oriented language (Python2 version)
 Python2, the high-level, interactive object oriented language,
 includes an extensive class library with lots of goodies for
 network programming, system administration, sounds and graphics.
 .
 This package is a dependency package, which depends on Debian's Python2
 version (currently v2.7).
Description-md5: 8a23c719c291789e6e4e8971b03680c5
```

---

### Post by MAFoElffen on 2021-10-31
I think I found where the oddity lies in this... Look at this query on the apt.log
```

mafoelffen@Mikes-ThinkPad-T520:~/Documents/Diagnostics$ grep -a3 'Breaks' Apt.log.test.txt
Starting pkgProblemResolver with broken count: 15
Starting 2 pkgProblemResolver with broken count: 15
Investigating (0) libsrt1.4-gnutls:amd64 < none -> 1.4.2-1.3 @un uN Ib >
Broken libsrt1.4-gnutls:amd64 Breaks on libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK >
  Considering libsrt1-gnutls:amd64 -3 as a solution to libsrt1.4-gnutls:amd64 21
  Added libsrt1-gnutls:amd64 to the remove list
  MarkDelete libsrt1-gnutls:amd64 < 1.4.1-5build1 @ii mK > FU=0
  Fixing libsrt1.4-gnutls:amd64 via remove of libsrt1-gnutls:amd64
Investigating (0) libtss2-esys-3.0.2-0:amd64 < none -> 3.0.3-2ubuntu1 @un uN Ib >
Broken libtss2-esys-3.0.2-0:amd64 Breaks on libtss2-esys0:amd64 < 3.0.1-1 @ii mK > (< 3.0.2-1)
  Considering libtss2-esys0:amd64 -9 as a solution to libtss2-esys-3.0.2-0:amd64 5
  Added libtss2-esys0:amd64 to the remove list
  MarkDelete libtss2-esys0:amd64 < 3.0.1-1 @ii mK > FU=0
  Fixing libtss2-esys-3.0.2-0:amd64 via remove of libtss2-esys0:amd64
Investigating (0) xfce4-helpers:amd64 < none -> 4.16.0-1ubuntu1 @un uN Ib >
Broken xfce4-helpers:amd64 Breaks on libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK >
  Considering libexo-helpers:amd64 -2 as a solution to xfce4-helpers:amd64 3
  Added libexo-helpers:amd64 to the remove list
  MarkDelete libexo-helpers:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK > FU=0
  Fixing xfce4-helpers:amd64 via remove of libexo-helpers:amd64
Investigating (0) python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
  Considering python-minimal:amd64 5096 as a solution to python2-minimal:amd64 1
  MarkKeep python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2-minimal:amd64 rather than change python-minimal:amd64
Investigating (0) libsidplayfp5:amd64 < none -> 2.0.5-2 @un uN Ib >
Broken libsidplayfp5:amd64 Breaks on libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK >
  Considering libsidplayfp4:amd64 -3 as a solution to libsidplayfp5:amd64 1
  Added libsidplayfp4:amd64 to the remove list
  MarkDelete libsidplayfp4:amd64 < 1.8.8-1build1 @ii mK > FU=0
--
  Considering python2:amd64 1 as a solution to python-is-python2:amd64 0
  Re-Instated python2-minimal:amd64
  Re-Instated python2:amd64
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Investigating (0) libboost1.74-dev:amd64 < none -> 1.74.0-8ubuntu2 @un uN Ib >
Broken libboost1.74-dev:amd64 Conflicts on libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU >
  Considering libboost1.71-dev:amd64 -1 as a solution to libboost1.74-dev:amd64 0
  Added libboost1.71-dev:amd64 to the remove list
  Conflicts//Breaks against version 1.71.0-6ubuntu9 for libboost1.71-dev but that is not InstVer, ignoring
  MarkDelete libboost1.71-dev:amd64 < 1.71.0-6ubuntu9 -> 1.71.0-6ubuntu11 @ii umU > FU=0
  Fixing libboost1.74-dev:amd64 via remove of libboost1.71-dev:amd64
Investigating (0) libmailutils6:amd64 < 1:3.9-3.2 @ii mK Ib >
--
  Removing libexo-1-0:amd64 rather than change libexo-helpers:amd64
  MarkDelete libexo-1-0:amd64 < 0.12.11-1ubuntu1.20.10.1 @ii mK Ib > FU=0
Investigating (1) python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib >
Broken python2-minimal:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb > (< 2.7.15-2)
  Considering python-minimal:amd64 5096 as a solution to python2-minimal:amd64 1
  MarkKeep python2-minimal:amd64 < none -> 2.7.18-2 @un umN Ib > FU=0
  Holding Back python2-minimal:amd64 rather than change python-minimal:amd64
--
Investigating (1) python-is-python2:amd64 < none -> 2.7.18-9 @un pumN Ib >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
  Considering python2:amd64 0 as a solution to python-is-python2:amd64 0
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Investigating (2) python-is-python2:amd64 < none -> 2.7.18-9 @un pumN Ib >
Broken python-is-python2:amd64 Depends on python2:amd64 < none | 2.7.18-2 @un umH >
  Considering python2:amd64 0 as a solution to python-is-python2:amd64 0
Broken python-is-python2:amd64 Breaks on python-minimal:amd64 < 2.7.1-0ubuntu2 @ii K NPb >
  Considering python-minimal:amd64 5096 as a solution to python-is-python2:amd64 0
Done
Log time: 2021-10-31 08:34:21.731489

```
You mentioned that at some point in time, and you were not sure when, that you updates stop working and you had some failures...

That output on the apt.log said that for some of those packages to updated successfully, that they needed to be "between" a certain version... Meaning they needed to be newer than a certain version, but also older than a certain version.That is probably where the packages first failed in the past...

The 20.10 repo's went dark, but... So you are in a loop. You have broken packages in your current installed version, that need a repository of what "you are" currently to correct/fix before you can do a release upgrade, but the supported repo's are now dark...

There are two choices for that... Migrate to a current version... Or go the unsupported way, to correct the current version by temporarily point the sources list to the "old-releases" repositories to correct/fix your current installation so you can do a do-release-upgrade.

Both ways involve "some work".

---

### Post by peyre on 2021-11-01
Oh boy.  I assume by "migrate" you mean to save off my data, reinstall the OS, and restore?  I can do that, though it'd involve a lot of work.

The other I'm not sure how to go about.

---

### Post by guiverc on 2021-11-01
You can *upgrade via re-install*; it's actually faster than a `do-release-upgrade` is; and works really well with packages that are sources from Ubuntu repositories.  It's just an install where you don't format, it causes the installer to do the following

- note your installed packages
- erase system directories (*this means some server apps will lose configs; but not an issue for desktop apps as they store configs in $HOME or the user directory*)
- install new system
- add back the additional *manually installed* (*noted earlier*) packages **if**available in the repositories for your new release
- won't touch any user files unless you formatted (where this install isn't used).

Alternatively, follow what MaFoElffen already suggested, the guide can be found here
- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
ie. just change `archive.ubuntu.com` to use `old-releases.ubuntu.com` and removing any country mirrors etc (none apply for old-releases; it's not mirrored).


Minor notes:

- You're using nvidia I gather; that should be catered for if you're using the Ubuntu packaged versions (*I didn't look*); the *upgrade via re-install* works well with Ubuntu packaged apps; 3rd party can give warnings of issues occurring; but these are usually easily fixed up post-install; if using 3rd party video drivers not from Ubuntu repositories; you may need to re-add them.

- If you're using an encrypted /home partition - those packages/encryption-option are no longer used default; so you need to add the package required for that prior to running the installer (*just add it before starting the install & it'll be good*).

- Backup anyway; it's easy to make a mistake with an install option & erase the system by mistake.

---

### Post by peyre on 2021-11-02
Ohh, a reinstall over the top would be brilliant!

So, I see the version I'm on is EOL.  So, I'm unclear on how to go about this.  Typically, the article isn't clear about how to actually do the upgrade.

---

### Post by guiverc on 2021-11-02
The link I provided was about EOL upgrades; ie. what was originally said here

> **MAFoElffen said:**
> 
The 20.10 repo's went dark, but... So you are in a loop. You have broken  packages in your current installed version, that need a repository of  what "you are" currently to correct/fix before you can do a release  upgrade, but the supported repo's are now dark...

There are two choices for that... Migrate to a current version... Or go  the unsupported way, to correct the current version by temporarily point  the sources list to the "old-releases"

It was the *official *link of how you make the `old-releases` change already suggested.  It's required to fix the package issues you have.

The purpose of that link is to make `sudo apt update`, `sudo apt full-upgrade` etc. return to functional **after** a release has gone EOL; allowing you to then fully-upgrade packages, correct any issues, and hopefully a `do-release-upgrade will then work.  :P

A re-install (*what I call 'upgrade via re-install'*) doesn't require this, as it erases the contents of system directories, so any package errors will be fixed. It won't however fix any user config errors are those aren't touched; thus remain.

When 20.10 reached EOL (*and I no longer needed the install for Lubuntu support purposes*); I performed a QA-test install onto that partition on one QA-test box and it became a 21.10 system; with my existing data files, even additional apps being re-installed (*I don't use the default music player but a different one; so that and my additional apps were re-installed*).  The fact that my example uses Lubuntu (not Xubuntu) makes no difference; it's just an indication that I'm on the Lubuntu team.

I have installs on that box which were 20.10, went to 21.04, 21.10, 20.04 ([*as 20.04.3 or a re-spin was coming out*]("https://fridge.ubuntu.com/2021/08/27/ubuntu-20-04-3-lts-released/")), back to [21.10]("https://fridge.ubuntu.com/2021/10/14/ubuntu-21-10-impish-indri-released/") & bounce around as installs happen; as I'm heavily involved in QA-testing (*and that includes Xubuntu!*)

---

### Post by peyre on 2021-11-02
So, I did a little searching on reinstalling over the top.  This site suggests you just boot with a copy of *buntu (it says a flash drive but I'd probably use a DVD), and hope there's a "Reinstall" option.  I assume I'd be using the same version I'm currently on (20.10).  Is this what you're suggesting?  If so that would be pretty slick!

[https://itsfoss.com/reinstall-ubuntu/](https://itsfoss.com/reinstall-ubuntu/)

---

### Post by guiverc on 2021-11-02
There used to be a 'repair' or 're-install' option but I haven't seen that for years (*near a decade*), but the key to triggering that type of install is not to format.

Use `*Something else*` (or `*Manual*` for Kubuntu, `*Manual Partitioning*` for Lubuntu/Ubuntu-Studio) and select your existing partitions; where you have a format checkbox - ensure that's **not ticked**.  It's the re-use of partition(s) (really the / partition) without format that triggers this type of install.

**It does notneed to be the same version**; which is why I call it *upgrade via re-install*. I mentioned a system where I bumped around releases (*the version order would have made no sense, but it was in the order of testing & actual releases..*) and I was trying to highlight you don't need the same release; in fact you can go *backwards* or *forwards*.  ie. **it'd allow you to return to the LTS (20.04) or go to the next release (21.04); or skip upgrades and go straight to (21.10)**...


There can be issues with going backwards... but that's rare.  example.  after 11.04 (*which I loved*) some new features came out in `evolution` or the GNOME MUA (mail program) that I decided to use as they helped me (*rules to color code emails as they reached inbox*). I soon decided I didn't like the upgrade (11.04->11.10) overall, so went back to the prior 11.04...  No issues; until I discovered some of my mail was using. Any email that had been color-coded by the newer features was ignored by the earlier program I was now using due to re-install, so the messages didn't show.. If I needed to reply to email from the couple of weeks that had been color-coded by the later version of the program, I had to copy the text of the email from the datafiles themselves as `evolution`ignored them.  When I next upgraded; the email returned to being visible/actionable. I'd used a later feature that created the problem when I returned to an earlier release that didn't have it.  ie. problems are rare; but can occur going backwards.  (*this example was from long ago - I can't think of a newer example*; *liferea changed database (format/storage) that causes complete loss at one point if you go backwards I think too, but I'll only notice it on programs that I use*).  To avoid issues you can read the application change-logs & thus predict (ie. homework; *release notes are where you start as they usually list apps & versions; then go to the program release notes themselves*), or just create a test system (VM etc) & test it yourself first; issues are rare & specific to the programs themselves - not the OS.

I'll provide a write up I did somewhat recently about the process; it wasn't geared at new users but those wanting to help us with QA (Quality Assurance) to explain the "*Install using existing partitions*" testcase we do with Lubuntu (*and what has me using this install weekly on average*) - [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743)

If a *release-upgrade* fails; the *upgrade via re-install* is my backup; though when I'm pressed for time, or have disk space issues, I tend to just use it (when 18.04 *flavors* reached EOL earlier this year, I used my own used boxes in QA-tests for a *focal* or 20.04.3 re-install; and actually used Xubuntu mostly for this.

---

### Post by peyre on 2021-11-02
I've done a little testing on the side here this morning, and if I have 20.10 installed then boot from a 20.10 DVD, it offers a Reinstall option.  Am I right that that would be ideal, or should I try **do-release-upgrade** first?  And then fall back to "Something else" (or something like that) if one/both of those fail?

Before doing any of this of course I'll boot with a Clonezilla CD and image my HD.  I might even run a backup (I back up to a portable drive a couple times a week) before getting started, though that would mean delaying the reinstall to tomorrow.

Incidentally, my system drive is an SSD and I have a second, mechanical, HD installed to hold most of my data, so some of my bets are already hedged here.

---

### Post by guiverc on 2021-11-02
Given you're on 20.10 now; I don't see what benefit you get from re-installing an EOL release.

Be it on thumb-drive, or DVD the options should be the same. 

I'm not very familiar with the option to which you refer; it's not a QA-test case ([http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/239079/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/429/builds/239079/testcases) for today's *jammy* for Xubuntu) so I haven't used it in years.

I just booted up a Xubuntu 21.10 ISO on the box besides me, and I don't see the option offered; but options do vary on the hardware/install capabilities of the machine you're using (*plus what's already on the box*). I'm unwilling to advise with that option, given I've not used it in years.

---

### Post by TheFu on 2021-11-02
Some tips for the future. You are getting excellent help from everyone above. I have nothing to add directly related, but ....

If you can't be bothered to upgrade in a timely way, only use LTS releases. Currently, that is 20.04. 22.04 will be ok to start testing for normal users around June and possibly for "production" use in late July.  New is the enemy of stable.

Trying to upgrade releases when the package manager is confused won't fix anything.  Ever.

A reinstall over an existing install is only scary if you didn't setup separate partitions for /home and all your data.  IF they are part of the main OS partition (/), I wouldn't trust that the method will 100% work with zero loss of data. I've never tried that - at least not recently.  I do remember losing all my data attempting something like that before Ubuntu existed.  Putting /home in a separate partition makes stuff like this much cleaner and less risky.

When trying to install stuff, there is a clear hierarchy of preferred methods to have a non-confused APT database.

[LIST]
[*]Canonical Repos
[*]Trusted Ubuntu PPAs (figuring out which PPAs are trustworthy enough to be used is a personal choice)
[*].deb file installs (but know that these can break dependencies and make your system get into a "can't update package" problem.) Avoid. If you do this, you'll need to manually upgrade the package at least weekly on your own, since APT likely won't know where to get updates.
[*]Snap Package - I'd avoid snaps for all sorts of reasons.  The few I've tried failed about 75% of the time - meaning if I installed 10 different snap packages, only 2 actually worked. The others didn't work or refused to start or had some missing dependency that is supposed to be impossible with snaps.
[*]Source code download and compile.  There are exceptions to this for scripted programs - like things written in python or perl. Perhaps ruby and GoLang and Java should still be avoided since those runtimes aren't included in stock Ubuntu. Again, if you go this way, then you'll manually want to check for updates each week.  For the few things like this I use, I've put them into my weekly patch script, so I don't forget.
[/LIST]


The management convenience of Linux systems with package management only works while we use the packages in the trusted repos.  As soon as we leave that 65,000 set of packages, we have decided to manually take on the task of patching and maintenance for those tools.  Trusted PPAs will keep up with the Canonical repos and update their programs within a few days after Canonical makes changes.  I have a few programs like that on a few systems - apertium is one example.  The PPA from the apertium team has been excellent.

And before doing anything like an OS upgrade always backup anything you cannot loose.  Any OS upgrade is like swapping the engine and transmission for your car. That's a big deal.  Without backups, you are using a blow-torch to remove the old engine and transmission, instead of unscrewing all the bolts, in the correct order, so you can put things back if something bad happens.

As for backups that can be used to upgrade a fresh OS install to the next version while having your settings (system and personal), there are lots of threads in these forums about that. Sorry, it isn't 1-click. It takes learning and effort, but it is very possible.  I moved a 16.04 32-bit desktop to 20.04 64-bit using the methods I've posted in these forums. All of it took less than an hour.

---

### Post by peyre on 2021-11-03
*Can't be bothered?*  The whole problem is the computer won't **do** the upgrade; I've asked it to several times.

I do know I'm getting good support here, and I'm grateful for it.

Well, notwithstanding the test I ran at the office, I didn't get a reinstall option, either with 20.10 or 21.10.  When I ran **sudo do-release-upgrade** it returned this at the end.  Looks familiar!

```
Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This was likely caused by: 
* Unofficial software packages not provided by Ubuntu 
Please use the tool 'ppa-purge' from the ppa-purge 
package to remove software from a Launchpad PPA and 
try the upgrade again. 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
```

---

### Post by TheFu on 2021-11-03
Call not do a release upgrade when normal updates aren't all working.

aptitude is a little smarter about trying different solutions and providing options.  It will offer multiple solutions to the dependency issues.  I usually reject the first 5-10, until it says one I recognize as removing some package I manually installed as a .deb file.  That manually installed .deb file almost certainly is holding back the normal updates that the Canonical repos would want. If I've declined them all, I do it again, this time rating the provided resolutions in my mind, picking the least bad.

However, just doing a fresh install of the new release will clear all those issues. Then I can restore selected settings for the system, daemons and all the personal stuff for every user from our daily backups.  There is an order for the restore of settings, data, then installation of previous manually installed packages (I make a list which gets included in the backups using apt-mark).  I don't think I'll ever do an "upgrade" if there are any issues with it at all. Installing fresh isn't THAT hard, with proper preparation. That preparation just happens to be the same as my normal backup and restore process, which is also the same base for disaster recovery.  Anything important has at least 1 additional copy.  Any data/settings that are changing often, will usually have 90-180 chances to be in backup sets over the last 90-180 days.

If you cannot figure out the dependency issue above, a fresh install is the only option.

---

### Post by peyre on 2021-11-03
Thanks TheFu.  I had a feeling I was doing the same thing at a command line that I'd been attempting through the GUI, given that the results were the same.

I'll look over what's installed and see if I did install something with a .deb that might have caused it, though I can't think of anything.  Still, it's been well over 6 months since this all started, so I might have done so and forgotten.

But it looks like I might have to do the clean install.  I've been really hoping not to do that.  On my laptops it would be no big deal, but my desktop will involve a *lot* of installing and configuring.  In preparation, I'm running a backup of all my data.

---

### Post by TheFu on 2021-11-03
> **peyre said:**
>  
But it looks like I might have to do the clean install.  I've been really hoping not to do that.  On my laptops it would be no big deal, but my desktop will involve a *lot* of installing and configuring.  In preparation, I'm running a backup of all my data.

If you used the package management system for all those installs, then you don't need to manually do it again. Just create a list of manually installed applications - **apt-mark showmanual** will output that list, so you just need to redirect it into a file and backup that file with the settings for those programs and personal settings.  If you get everything /etc/ in your backup, you'll have all the system settings worth your time.  

If you compiled programs and installed those, hopefully, you placed them into /usr/local/ ... back that up.

All your personal settings and those for each different userid are in the userid's HOME directory, where ever that is. For humans, it is typically /home/{username}, but it can be anywhere. The password db/file has that information. It is just text, so look at it. Now you just need the data in the backup.
[LIST]
[*]Fresh install ~ 15 min
[*]Restore system and personal settings ~ 5 min (need to be selective with stuff in /etc/ ... don't just install everything. I put comments in every file I modify so they are easy to find later.  Something like:
```
# :BACKUP:
```
[*]Restore system and personal data ~ 15 min
[*]Feed the list of manually installed packages into APT - they see the prior settings and they see the data. To them, it looks like a package reinstall ~ 5 min
[/LIST]
In under 60 minutes, you've done a fresh install, retained your settings and data and reinstalled probably 95% of the packages on the system. It feels like "your system" again.

Of course, if you don't have automatic backups which capture this data already, effort and time to set that up is necessary. There's no magic bullet with this stuff. Also, expect the backup files to need a few attempts to get all of them - took me about 5 failed restore attempts before I had everything I needed included in the backups.  I also create daily point-n-time data captures. For example, I create a machine readable copy of partition tables, since a corrupted partition table can make for a really bad day. The file is tiny, so why not have it as insurance?  I also get everything under /etc/ ... retaining the owner, group, permissions, xattrs and ACLs.  That requires a real backup tool running as root. Cannot just copy stuff off.

If you use non-APT packages, how to backup and restore those is on you.  For example, snap packages that have been forced onto us.  **snap list > snap-list** will probably get the list. I avoid snaps, so that list is fairly short and really only 1-3 packages matter to me. The others are not used often enough that I wouldn't just wait to install them as needed.  I don't install .deb files manually on most of my systems. Just not something I do.  I do install some scripts that have a self-upgrade capability.  Those are in my backups and weekly patch scripts.

Initially, I had just the core stuff. Over time, I've added more "nice to have" information to my backups. For example:
```
apt-mark.auto    cpan.list     df.txt     inxi.out  lvs.txt        pvs.txt
apt-mark.manual  crontab.thefu    dpkg.list  lshw.list        parted.txt     vgdisplay.txt
blkid.txt        crontab.root  gem.list   lvdisplay.txt    pvdisplay.txt  vgs.txt
```
Really, only the apt-mark.manual and crontab* files are needed for a proper restore.

---

### Post by peyre on 2021-11-03
Wow, sounds much more clever and surgical and efficient than my old way, brought over from my Windows days.  I'll go with that.  So what would you recommend to use as a real backup tool for /etc?  I generally do my backups by running a script that copies files & folders to the portable drive - that way they're easily accessible anywhere.

Being selective about what to restore in /etc...sounds like good advice but I don't know what to select and what to leave off.

However, I just ran **apt-mark showmanual** on my laptop here, which doesn't have an awful lot of things I installed manually, and it returned a *huge* list that scrolled past the limit of my terminal window.  Everything before L is cut off.  Sounds like it might be easier to just use Software to make a list of what I installed.

Edit: I reran the command and sent it to a text file.  It has 1,490 lines showing, including very system-related things like xubuntu-core and xserver-core.  

I haven't used snaps yet, as far as I know.

---

