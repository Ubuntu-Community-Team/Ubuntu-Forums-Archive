---
title: "Unmet dependencies, &quot;E: Sub-process /usr/bin/dpkg returned an error code (1)&quot;"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by herdpoisoningmedia on 2013-09-28
Update manager will not let me go any further.

I get the details:

The following packages have unmet dependencies:

libhx509-5-heimdal: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is installed
                    Depends: libcomerr2 (>= 1.34) but 1.42-1ubuntu2 is installed
libhx509-5-heimdal:i386: Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.4 is installed
                         Depends: libcomerr2 (>= 1.34) but 1.42-1ubuntu2 is installed

I run sudo apt-get install -f and get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libhx509-5-heimdal:i386
The following packages will be upgraded:
  libhx509-5-heimdal:i386
1 upgraded, 0 newly installed, 0 to remove and 140 not upgraded.
8 not fully installed or removed.
Need to get 0 B/127 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libhx509-5-heimdal:i386 (--configure):
 libhx509-5-heimdal:i386 1.6~git20120311.dfsg.1-2 cannot be configured because libhx509-5-heimdal:amd64 is in a different version (1.6~git20120311.dfsg.1-2ubuntu0.1)
dpkg: error processing libhx509-5-heimdal (--configure):
 libhx509-5-heimdal:amd64 1.6~git20120311.dfsg.1-2ubuntu0.1 cannot be configured because libhx509-5-heimdal:i386 is in a different version (1.6~git20120311.dfsg.1-2)
dpkg: dependency problems prevent configuration of libkrb5-26-heimdal:
 libkrb5-26-heimdal depends on libhx509-5-heimdal (>= 1.4.0+git20110226); however:
  Package libhx509-5-heimdal is not configured yet.
dpkg: error processing libkrb5-26-heimdal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-26-heimdal:i386:
 libkrb5-26-heimdal:i386 depends on libhx509-5-heimdal (>= 1.4.0+git20110226); however:
  Package libhx509-5-heimdal:i386 is not configured yet.
dpkg: error processing libkrb5-26-heimdal:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libheimntlm0-heimdal:i386:
 libheimntlm0-heimdal:i386 depends on libkrb5-26-heimdal (>= 1.4.0+git20110226); however:
  Package libkrb5-26-heimdal:i386 is not configured yet.
dpkg: error processing libheimntlm0-heimdal:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configurNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                    No apport report written because the error message indicates its a followup error from a previous failure.
              No apport report written because MaxReports is reached already
                                                                            ation of libheimntlm0-heimdal:
 libheimntlm0-heimdal depends on libkrb5-26-heimdal (>= 1.4.0+git20110226); however:
  Package libkrb5-26-heimdal is not configured yet.
dpkg: error processing libheimntlm0-heimdal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi3-heimdal:
 libgssapi3-heimdal depends on libheimntlm0-heimdal (>= 1.4.0+git20110226); however:
  Package libheimntlm0-heimdal is not configured yet.
 libgssapi3-heimdal depends on libkrb5-26-heimdal (>= 1.4.0+git20110403); however:
  Package libkrb5-26-heimdal is not configured yet.
dpkg: error processing libgssapi3-heimdal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgssapi3-heimdal:i386:
 libgssapi3-heimdal:i386 depends on libheimntlm0-heimdal (>= 1.4.0+git20110226); however:
  Package libheimntlm0-heimdal:i386 is not configured yet.
 libgssapi3-heimdal:i386 depends on libkrb5-26-heimdal (>= 1.4.0+git20110403); however:
  Package libkrb5-26-heimdal:i386 is not configured yet.
dpkg: error processing libgssapi3-heimdal:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libhx509-5-heimdal:i386
 libhx509-5-heimdal
 libkrb5-26-heimdal
 libkrb5-26-heimdal:i386
 libheimntlm0-heimdal:i386
 libheimntlm0-heimdal
 libgssapi3-heimdal
 libgssapi3-heimdal:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have been trying to work through this without begging for help for a few weeks, but figured I should prostrate myself at the altar of community support and beg for assistance before I reformat and reinstall.  Any suggestions?

---

### Post by ubfan1 on 2013-09-28
Looks like a bad depends got entered:
libhx509-5-heimdal:i386: Depends: libc6 (>= 2.8) but 2.15-0ubuntu10.4 is installed
2.8 ????   Both i386 and 64bit should be the 2.15 version.  File a bug against the package?
You do have all the other ia32 libraries and multiarch packages installed don't you?

---

### Post by herdpoisoningmedia on 2013-09-29
I apparently did not have ia32-libs installed, so I installed through Synaptic, but am still getting the same error. I seem to have all the multiarch files in Synaptic except binutils-multiarch.  

As far as filing a bug report, it looks like there is an update available in the install manager already, but I cannot install it as I get this same error with anything I try to update through the install manager.   

(I did just notice that I can install at least some things through Synaptic, so I will try that and see if it somehow works)

---

### Post by ubfan1 on 2013-09-29
Specifically I was thinking of the ia32-libs-multiarch package (which for some reason does not seem to show in the apt-cache pkgnames output:
apt-cache show ia32-libs-multiarch
Package: ia32-libs-multiarch
Priority: extra
Section: universe/libs
Installed-Size: 39
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ia32-libs
Version: 20090808ubuntu36
...
Description-en: Multi-arch versions of former ia32-libraries
 This package depends on i386 versions of packages that were removed from
 ia32-libs and transitioned to multi-arch.  This allows applications using
 ia32-libs in previous Ubuntu releases to continue functioning without missing
 libraries.

---

### Post by herdpoisoningmedia on 2013-09-30
Here is my output for  apt-cache show ia32-libs-multiarch
Package: ia32-libs-multiarch
Priority: extra
Section: universe/libs
Installed-Size: 39
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ia32-libs
Version: 20090808ubuntu36
Depends: bluez-alsa, libgettextpo0, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-oxygen, gvfs, ibus-gtk, libacl1, libaio1, libao4, libasound2, libasound2-plugins, libasyncns0, libattr1, libaudio2, libcanberra-gtk-module, libcap2, libcapi20-3, libcups2, libcupsimage2, libcurl3, libdbus-glib-1-2, libesd0, libfontconfig1, libfreetype6, libgail-common, libgconf-2-4, libgdbm3, libglapi-mesa, libglu1-mesa, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libmpg123-0, libncursesw5, libnspr4, libnss3, libodbc1, libopenal1, libpulse-mainloop-glib0, libqt4-dbus, libqt4-network, libqt4-opengl, libqt4-qt3support, libqt4-script, libqt4-scripttools, libqt4-sql, libqt4-svg, libqt4-test, libqt4-xml, libqt4-xmlpatterns, libqtcore4, libqtgui4, libqtwebkit4, librsvg2-common, libsane, libsdl-mixer1.2, libsdl-image1.2, libsdl-net1.2, libsdl-ttf2.0-0, libsdl1.2debian, libsqlite3-0, libssl0.9.8, libssl1.0.0, libstdc++5, libstdc++6, libxaw7, libxml2, libxp6, libxslt1.1, libxss1, libxtst6, odbcinst1debian2, libpulsedsp, xaw3dg
Recommends: libgl1-mesa-glx, libgl1-mesa-dri
Suggests: libpam-ldap, libpam-winbind, libnss-ldap
Filename: pool/universe/i/ia32-libs/ia32-libs-multiarch_20090808ubuntu36_i386.deb
Size: 4682
MD5sum: 326c052b5fe589b730fa67499a463384
SHA1: e296b805dc98cd7ac307b838f9a5e977b13931c8
SHA256: 171b4f9078df3b73228862e728278e59b621ed46c1611516958fd68c68239ae4
Description-en: Multi-arch versions of former ia32-libraries
 This package depends on i386 versions of packages that were removed from
 ia32-libs and transitioned to multi-arch.  This allows applications using
 ia32-libs in previous Ubuntu releases to continue functioning without missing
 libraries.
Multi-Arch: foreign
Description-md5: 2dfb3546bc498438a76638f4fcd00b0c
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: ia32-libs-multiarch
Priority: extra
Section: universe/libs
Installed-Size: 39
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ia32-libs
Version: 20090808ubuntu35
Depends: bluez-alsa, libgettextpo0, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-fluendo-mp3, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-oxygen, gvfs, ibus-gtk, libacl1, libaio1, libao4, libasound2, libasound2-plugins, libasyncns0, libattr1, libaudio2, libcanberra-gtk-module, libcap2, libcapi20-3, libcups2, libcupsimage2, libcurl3, libdbus-glib-1-2, libesd0, libfontconfig1, libfreetype6, libgail-common, libgconf-2-4, libgdbm3, libglapi-mesa, libglu1-mesa, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libmpg123-0, libncursesw5, libnspr4, libnss3, libodbc1, libopenal1, libpulse-mainloop-glib0, libqt4-dbus, libqt4-network, libqt4-opengl, libqt4-qt3support, libqt4-script, libqt4-scripttools, libqt4-sql, libqt4-svg, libqt4-test, libqt4-xml, libqt4-xmlpatterns, libqtcore4, libqtgui4, libqtwebkit4, librsvg2-common, libsane, libsdl-mixer1.2, libsdl-image1.2, libsdl-net1.2, libsdl-ttf2.0-0, libsdl1.2debian, libsqlite3-0, libssl0.9.8, libssl1.0.0, libstdc++5, libstdc++6, libxaw7, libxml2, libxp6, libxslt1.1, libxss1, libxtst6, odbcinst1debian2, libpulsedsp, xaw3dg
Recommends: libgl1-mesa-glx, libgl1-mesa-dri
Suggests: libpam-ldap, libpam-winbind, libnss-ldap
Filename: pool/universe/i/ia32-libs/ia32-libs-multiarch_20090808ubuntu35_i386.deb
Size: 4554
MD5sum: cda17f80e8c2c7e8ed79390c6462d184
SHA1: 108d0a21f7889331105afeb0a86dad9f3da2d90c
SHA256: 93045368d952407c927000ec582b573bf27b367cc13a06d8a9a6f786dd7818e4
Description-en: Multi-arch versions of former ia32-libraries
 This package depends on i386 versions of packages that were removed from
 ia32-libs and transitioned to multi-arch.  This allows applications using
 ia32-libs in previous Ubuntu releases to continue functioning without missing
 libraries.
Multi-Arch: foreign
Description-md5: 2dfb3546bc498438a76638f4fcd00b0c
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu


Looks like I have an older version (35 instead of 36)
I am admittedly in over my head here, so if this is not what you were asking for I apologize (and thank you for the help)

---

### Post by ubfan1 on 2013-09-30
Looks like the md5sums are the same, so they're the same.  The apt-cache show ... shows what's available, not what's installed.  What does the dpkg -l  | grep multi   show?  I have things like:
 un  ia32-libs-multiarch      <none>                   (no description available)
ii  krb5-multidev            1.10+dfsg~beta1-2ubuntu0 Development files for MIT Kerberos without Heimdal conflict
un  libgl1-mesa-glx-no-multi <none>                   (no description available)
ii  multiarch-support        2.15-0ubuntu10.4         Transitional package to ensure multiarch compatibility
But I've never done anything with Kerberos or Heimdal.

---

### Post by herdpoisoningmedia on 2013-09-30
Output of dpkg -l  | grep multi

ii  balazar3-3d                            0.1-10                                              dungeon adventure game with multiplayer support - 3D version
ii  balazar3-common                        0.1-10                                              dungeon adventure game with multiplayer support - common files
ii  basket                                 2.0~beta2-0ubuntu2                                  a multi-purpose note-taking application for KDE
ii  empathy                                3.4.2.3-0ubuntu1                                    GNOME multi-protocol chat and call client
ii  empathy-common                         3.4.2.3-0ubuntu1                                    GNOME multi-protocol chat and call client (common files)
ii  festival                               1:2.1~release-1ubuntu2                              General multi-lingual speech synthesis system
ii  gdb-multiarch                          7.4-2012.04-0ubuntu2.1                              The GNU Debugger (with support for multiple architectures)
ii  gstreamer0.10-plugins-bad-multiverse   0.10.21-1                                           GStreamer plugins from the "bad" set (Multiverse Variant)
ii  ia32-libs-multiarch:i386               20090808ubuntu36                                    Multi-arch versions of former ia32-libraries
ii  jackeq                                 0.5.9-2                                             routes and manipulates audio from/to multiple sources
ii  jamin                                  0.97.14~cvs~81203-4                                 Audio mastering from a mixed down multitrack source with JACK
ii  jokosher                               0.11.5-5                                            simple and easy to use audio multi-tracker
ii  kdemultimedia-kio-plugins              4:4.8.5-0ubuntu1                                    transparent audio CD access for applications using the KDE Platform
ii  krb5-multidev                          1.10+dfsg~beta1-2ubuntu0.3                          Development files for MIT Kerberos without Heimdal conflict
ii  libanyevent-perl                       6.120-1                                             event loop framework with multiple implementations
ii  libboost-thread1.46.1                  1.46.1-7ubuntu3                                     portable C++ multi-threading
ii  libgmerlin-avdec1                      1.1.0~dfsg-3build1                                  general multimedia decoding library
ii  libgrip0                               0.3.5-0ubuntu1~12.04.1                              provides multitouch gestures to GTK+ apps
ii  libgstreamermm-0.10-2                  0.10.9-1                                            C++ wrapper library for the multimedia library GStreamer (shared libraries)
ii  libimage-exiftool-perl                 8.60-2                                              Library and program to read and write meta information in multimedia files
ii  libkephal4abi1                         4:4.8.5-0ubuntu0.3                                  API for easier handling of multihead systems
ii  liblqr-1-0                             0.4.1-1.1                                           converts plain array images into multi-size representation
ii  libm17n-0                              1.6.3-1                                             multilingual text processing library - runtime
ii  libmlt++3                              0.7.6+git20120204-2                                 MLT multimedia framework C++ wrapper (runtime)
ii  libmlt-data                            0.7.6+git20120204-2                                 multimedia framework (data)
ii  libmlt4                                0.7.6+git20120204-2                                 multimedia framework (runtime)
ii  libmpc2                                0.9-4                                               multiple precision complex floating-point library
ii  libmpfr4                               3.1.0-3ubuntu2                                      multiple precision floating-point computation
ii  libphonon4                             4:4.7.0really4.6.0-0ubuntu1                         multimedia framework from KDE - core library
ii  libpurple-bin                          1:2.10.3-0ubuntu1.3                                 multi-protocol instant messaging library - extra utilities
ii  libpurple0                             1:2.10.3-0ubuntu1.3                                 multi-protocol instant messaging library
ii  libqtmultimediakit1                    1.2.0-1ubuntu2                                      Qt Mobility MultimediaKit module
ii  libsane-hpaio                          3.12.2-1ubuntu3.2                                   HP SANE backend for multi-function peripherals
ii  libtommath0                            0.42.0-1                                            multiple-precision integer library [runtime]
ii  libusbmuxd1                            1.0.7-2ubuntu0.1                                    USB multiplexor daemon for iPhone and iPod Touch devices - library
ii  libvlc5                                2.0.8-0ubuntu0.12.04.1                              multimedia player and streamer library
ii  m17n-contrib                           1.1.13-1                                            multilingual text processing library - contributed database
ii  m17n-db                                1.6.3-1                                             multilingual text processing library - database
ii  megaglest                              3.6.0.3-1ubuntu1                                    3D multi-player real time strategy game
ii  multiarch-support                      2.15-0ubuntu10.4                                    Transitional package to ensure multiarch compatibility
ii  mx44                                   1.0-0ubuntu5                                        polyphonic, multichannel midi realtime software synthesizer
ii  nautilus-sendto-empathy                3.4.2.3-0ubuntu1                                    GNOME multi-protocol chat and call client (nautilus-sendto plugin)
ii  ogmtools                               1:1.5-3ubuntu1                                      Tools for manipulating Ogg multimedia streams
ii  phonon                                 4:4.7.0really4.6.0-0ubuntu1                         multimedia framework from KDE - metapackage
ii  pidgin                                 1:2.10.3-0ubuntu1.3                                 graphical multi-protocol instant messaging client for X
ii  pidgin-data                            1:2.10.3-0ubuntu1.3                                 multi-protocol instant messaging client - data files
ii  postgresql-client-common               129ubuntu1                                          manager for multiple PostgreSQL client versions
ii  python-mlt3                            0.7.6+git20120204-2                                 multimedia framework (python bindings)
ii  qtractor                               0.5.4-1                                             MIDI/Audio multi-track sequencer application
ii  usbmuxd                                1.0.7-2ubuntu0.1                                    USB multiplexor daemon for iPhone and iPod Touch devices
ii  vlc                                    2.0.8-0ubuntu0.12.04.1                              multimedia player and streamer
ii  vlc-nox                                2.0.8-0ubuntu0.12.04.1                              multimedia player and streamer (without X support)

(most of which is completely irrelevant I am pretty sure)

I am not even sure what Kerberos or Heimdal do  (I have looked them up, but am still lost).  I would just try to remove it, but Synaptec says to remove it it needs to also remove a zillion other things that I do use as they are dependent on it.  (I'm guessing wildly that it has something to do with the Ubuntu Install Manager, and removing it would remove anything I installed through that.)  

I should mention that reformatting and reinstalling is very much an option, so unless you enjoy a good puzzle, I can always just go that route ;)

---

### Post by fmarinheiro on 2013-10-01
Recently i had a similar problem but it was with a different package and this was the only way to fix it.

sudo dpkg --force-all -P <package>

---

### Post by ubfan1 on 2013-10-01
Did you run apt-get update  first?

---

### Post by fmarinheiro on 2013-10-01
> **ubfan1 said:**
> Did you run apt-get update  first?

I was having the same problem with libgssapi3-heimdal can't remember much more details but i think it was the same problem as you are having.

I did apt-get update than apt-get upgrade and got that gigantic stack of errors, after the i could not update the system nor install anything at all. 

apt-get install -f gave me the same problem

Than i've run sudo dpkg --force-all -P libgssapi3-heimda and then my ubuntu started working normally again.

---

### Post by herdpoisoningmedia on 2013-10-01
I tried apt-get update and apt-get upgrade as well with the same errors
I will try the sudo dpkg --force-all -P libhx509-5-heimdal:i386
followed by the other packages and cross my fingers and post the results if I have not killed my system entirely (it sounds scary).

---

### Post by herdpoisoningmedia on 2013-10-02
w00h00!
I did 
sudo dpkg --force-all -P libhx509-5-heimdal:i386
sudo apt-get install -f
And it worked!
I am now getting updated through update manager and my system seems all nice and happy now!!!
Thank you so very very very much!!  You guys/gals rock!

---

### Post by fmarinheiro on 2013-10-02
> **herdpoisoningmedia said:**
> w00h00!
I did 
sudo dpkg --force-all -P libhx509-5-heimdal:i386
sudo apt-get install -f
And it worked!
I am now getting updated through update manager and my system seems all nice and happy now!!!
Thank you so very very very much!!  You guys/gals rock!

Nice to know it worked.

I know it is a little drastic solution but the system wasn't working for me anyway. 
I couldn't remove or install anything and took the chance :)

---

