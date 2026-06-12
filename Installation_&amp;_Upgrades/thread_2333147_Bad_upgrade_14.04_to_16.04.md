---
title: "Bad upgrade 14.04 to 16.04"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2016-08-07
I have Ubuntu 14.04.5 x64 on my desktop which has an Intel I5-3750K with 32GB of memory.  I just tried to upgrade from 14.04 to 16.04.  The upgrade indicated several errors along the way.  At one point, I received a message saying my system was unstable.  Finally, I received a message saying the upgrade could not be completed and a Recovery process was being executed.  This was all on the Upgrade step of the process.  When the Recovery process completed, I received a message saying the upgrade was complete.  At this point the upgrade process ended.  The Cleanup process never executed, and I was never asked to Reboot.  I am now in my 14.04 DE (Gnome Fallback), and my kernel shows as 3.13.0-92 (my last installed 14.04 kernel), and my distribution is showing 16.04.1.  I can execute all my user programs as before, but most (if not all) of the Systems programs will not run.  I have a backup of my Ubuntu partition prior to starting the upgrade.  Any suggestions on how I should proceed?

---

### Post by Bucky Ball on 2016-08-07
Try this. If you have installed any PPAs manually disable them, then:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot.

---

### Post by cscj01 on 2016-08-07
Should I do this in my current DE?

I started with the first command```
sudo apt-get autoremove
```It quit with the following messages:```
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```There were many errors related to dpkg with dependency problems. here is the complete terminal output:```
sudo apt-get autoremove
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  account-plugin-twitter aptitude-common baloo-kf5 bbswitch-dkms catdoc
  checkbox-ng dolphin friends friends-dispatcher friends-facebook
  friends-twitter g++-4.8 gcc-4.8-base:i386 gcc-4.9-base gcc-4.9-base:i386
  gcj-4.8-jre-lib gir1.2-clutter-gst-2.0 gir1.2-ebook-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-gtkclutter-1.0
  gir1.2-messagingmenu-1.0 gpsd gstreamer1.0-clutter gstreamer1.0-gnonlin
  kubuntu-debug-installer latex-beamer latex-xcolor libapt-inst1.5
  libapt-pkg4.12 libarchive-extract-perl libastro1 libatk-wrapper-java
  libatk-wrapper-java-jni libavahi-client-dev libavahi-common-dev
  libavdevice53 libavfilter3 libavresample1 libbaloowidgets4
  libbasicusageenvironment0 libbind9-90 libboost-date-time1.54.0
  libboost-filesystem1.54.0 libboost-iostreams1.54.0 libboost-locale1.54.0
  libboost-python1.54.0 libboost-regex1.54.0 libboost-signals1.54.0
  libboost-system1.54.0 libboost-thread1.54.0 libcamel-1.2-45 libcdr-0.0-0
  libcgmanager0:i386 libclass-load-perl libcmis-0.4-4 libcolorhug1
  libcrypt-passwdmd5-perl libcuda1-349 libdata-optlist-perl libdbd-mysql-perl
  libdns100 libdolphinvcs5 libdvbpsi8 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libedata-book-1.2-20 libedataserver-1.2-18
  libegl1-mesa-drivers libelfg0 libept1.4.12 libepub0 libestools2.1
  libfarstream-0.1-0 libfriends0 libgcj14 libgcrypt11-dev libgcrypt20-dev
  libgdata13 libglamor0 libglewmx1.10 libgnome-bluetooth11
  libgnome-desktop-3-7 libgnutlsxx27 libgpg-error-dev libgphoto2-dev
  libgphoto2-port10 libgphoto2-port10:i386 libgps20 libgps22 libgroupsock1
  libicc2 libidl-common libieee1284-3-dev libimdi0 libimobiledevice4 libisc95
  libisccc90 libisccfg90 libisl10 libjson0 libkactivities-models1 libkf5baloo5
  libkf5balooengine5 libkf5baloowidgets-bin libkf5baloowidgets5
  libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3
  libkf5kcmutils-data libkf5kcmutils5 libkf5parts-data libkf5parts-plugins
  libkf5parts5 libkfilemetadata4 libkgeomap-data libkidletime4 liblinear1
  liblivemedia23 liblmdb0 liblog-message-perl liblog-message-simple-perl
  liblouis2 liblwres90 libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmarblewidget-qt5-23 libmbim-glib0 libmikmod2 libminiupnpc8
  libmodule-pluggable-perl libmono-csharp4.0c-cil
  libmono-microsoft-csharp4.0-cil libmrm4 libmspub-0.0-0 libmusicbrainz5-0
  libmysqlclient18 libnepomukcleaner4 libnepomukcore4abi1 libnih-dbus1:i386
  libnih1:i386 liborcus-0.6-0 libpano13-2 libpocketsphinx1 libpod-latex-perl
  libpod-plainer-perl libpoppler-private-dev libpoppler-qt4-4 libpoppler44
  libprocps3 libprotobuf8 libprotoc8 libpth20 libqapt3 libqapt3-runtime
  libqextserialport1 libqmi-glib0 libqmobipocket1 libqpdf13
  libqt5qml-graphicaleffects libqt5sensors5 libqt5webkit5-qmlwebkitplugin
  libqtlocation1 libqtscript4-core libqtscript4-gui libqtscript4-network
  libqtscript4-uitools libqtscript4-xml libquazip0 libraw9 librhythmbox-core8
  librpmsign1 librtaudio4 librtmidi1 libservlet3.0-java libshp1 libshp2
  libsoprano4 libsphinxbase1 libspice-server1 libstk0c2a libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtagc0 libterm-ui-perl
  libtext-soundex-perl libthumbnailer0 libtinyxml2-0.0.0 libuil4
  libunityvoice1 libusageenvironment1 libusb-1.0-0-dev libusb-1.0-doc
  libusbmuxd2 libvisio-0.0-0 libvpx1:i386 libwebkit2gtk-3.0-25 libwlocate0
  libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libxcb-util0 libxt-dev libxtables10
  libzip2 libzthread-2.3-2 lsb-cxx lsb-desktop lsb-graphics lsb-languages
  lsb-multimedia marble-data marble-plugins mono-mcs nepomuk-core-data
  nvidia-prime pgf python-commandnotfound python-cycler python-dateutil
  python-dbus-dev python-gst-1.0 python-matplotlib python-tz python3-checkbox
  python3-icu qapt-batch qml-module-qtquick-localstorage
  qml-module-ubuntu-ui-extras-browser qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin ruby-vte ruby-vte3 soprano-daemon
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en texlive-luatex
  unity-lens-friends unity-scope-audacious unity-scope-clementine
  unity-scope-gmusicbrowser unity-scope-gourmet unity-scope-guayadeque
  unity-scope-musique unity-voice-service
0 upgraded, 0 newly installed, 254 to remove and 1 not upgraded.
1031 not fully installed or removed.
After this operation, 447 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 670244 files and directories currently installed.)
Removing friends-twitter (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing account-plugin-twitter (0.12+16.04.20160126-0ubuntu1) ...
Removing dolphin (4:15.12.3-0ubuntu1) ...
Removing libkf5baloowidgets-bin (4:15.12.3-0ubuntu1) ...
Removing baloo-kf5 (5.18.0-0ubuntu1.1) ...
Removing nvidia-prime (0.8.2) ...
Removing bbswitch-dkms (0.8-3ubuntu1) ...
Removing checkbox-ng (0.23-2) ...
Removing g++-4.8 (4.8.5-4ubuntu2) ...
Removing unity-lens-friends (0.1.3+14.04.20140317-0ubuntu1) ...
Removing libfriends0:amd64 (0.1.2+14.04.20131108.1-0ubuntu1) ...
Removing friends-facebook (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing friends (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing friends-dispatcher (0.2.0+14.04.20140217.1-0ubuntu1) ...
Removing gir1.2-ebook-1.2:amd64 (3.18.5-1ubuntu1) ...
Removing gir1.2-ebookcontacts-1.2:amd64 (3.18.5-1ubuntu1) ...
Removing gir1.2-edataserver-1.2:amd64 (3.18.5-1ubuntu1) ...
Removing gpsd (3.15-2build1) ...
Removing kubuntu-debug-installer (16.04ubuntu2) ...
Removing libclass-load-perl (0.23-1) ...
Removing libfarstream-0.1-0:amd64 (0.1.2-3ubuntu1) ...
Removing libkf5baloowidgets5:amd64 (4:15.12.3-0ubuntu1) ...
Removing libkf5baloo5 (5.18.0-0ubuntu1.1) ...
Removing libkf5kcmutils5:amd64 (5.18.0-0ubuntu1) ...
Removing libkf5parts-plugins (5.18.0-0ubuntu1) ...
Removing libkf5parts5:amd64 (5.18.0-0ubuntu1) ...
Removing libbaloowidgets4 (4:4.13.3-0ubuntu0.1) ...
Removing libkfilemetadata4 (4:4.14.2-0ubuntu2) ...
Removing libkidletime4 (4:4.14.16-0ubuntu3) ...
Removing mono-mcs (4.2.1.102+dfsg2-7ubuntu4) ...
Removing libmono-microsoft-csharp4.0-cil (4.2.1.102+dfsg2-7ubuntu4) ...
Removing libmono-csharp4.0c-cil (4.2.1.102+dfsg2-7ubuntu4) ...
Removing libpoppler-qt4-4:amd64 (0.41.0-0ubuntu1) ...
Removing libqmobipocket1 (4:15.12.3-0ubuntu1) ...
Removing libkactivities-models1 (4:4.13.3-0ubuntu0.2) ...
Removing libnepomukcore4abi1 (4:4.13.3-0ubuntu0.2) ...
Removing libsoprano4 (2.9.4+dfsg1-0ubuntu3) ...
Removing python-commandnotfound (0.3ubuntu16.04.2) ...
Removing python3-icu (1.9.2-2build1) ...
Removing qapt-batch (3.0.2-0ubuntu1.1) ...
Removing qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 (0.23+16.04.20160413-0ubuntu1) ...
Removing qml-module-ubuntu-ui-extras-browser:amd64 (0.23+16.04.20160413-0ubuntu1) ...
Removing soprano-daemon (2.9.4+dfsg1-0ubuntu3) ...
Removing texlive-luatex (2015.20160320-1) ...
Removing libebook-1.2-14 (3.10.4-0ubuntu1.5) ...
Removing libedata-book-1.2-20 (3.10.4-0ubuntu1.5) ...
Removing libebook-contacts-1.2-0 (3.10.4-0ubuntu1.5) ...
Removing python3-checkbox (0.17.6-0ubuntu6) ...
Removing libkf5filemetadata-bin:amd64 (5.18.0-0ubuntu1) ...
Removing libkf5filemetadata3:amd64 (5.18.0-0ubuntu1) ...
Removing libkf5filemetadata-data (5.18.0-0ubuntu1) ...
Removing latex-beamer (3.24-1) ...
Removing pgf (2.10-1) ...
Removing aptitude-common (0.7.4-2ubuntu2) ...
Removing catdoc (1:0.94.3~git20160113.dbc9ec6+dfsg-1) ...
Removing gcc-4.8-base:i386 (4.8.5-4ubuntu2) ...
Removing gcc-4.9-base:i386 (4.9.3-13ubuntu2) ...
Removing gcc-4.9-base:amd64 (4.9.3-13ubuntu2) ...
Removing gcj-4.8-jre-lib (4.8.5-4ubuntu2) ...
Removing gir1.2-clutter-gst-2.0 (2.0.18-1) ...
Removing gir1.2-gtkclutter-1.0:amd64 (1.6.6-1) ...
Removing gir1.2-messagingmenu-1.0 (13.10.1+15.10.20150505-0ubuntu1) ...
Removing gstreamer1.0-clutter (2.0.18-1) ...
Removing gstreamer1.0-gnonlin (1.2.0-1) ...
Removing latex-xcolor (2.11-1.1) ...
Removing libapt-inst1.5:amd64 (1.0.1ubuntu2.14) ...
Removing libept1.4.12:amd64 (1.0.12) ...
Removing libapt-pkg4.12:amd64 (1.0.1ubuntu2.14) ...
Removing libarchive-extract-perl (0.76-1) ...
Removing marble-plugins (4:15.12.3-0ubuntu2) ...
Removing libmarblewidget-qt5-23 (4:15.12.3-0ubuntu2) ...
Removing libastro1 (4:15.12.3-0ubuntu2) ...
Removing libatk-wrapper-java-jni:amd64 (0.33.3-6) ...
Removing libatk-wrapper-java (0.33.3-6) ...
Removing libavahi-client-dev (0.6.32~rc+dfsg-1ubuntu2) ...
Removing libavahi-common-dev (0.6.32~rc+dfsg-1ubuntu2) ...
Removing libavdevice53:amd64 (6:9.18-0ubuntu0.14.04.1) ...
Removing libavfilter3:amd64 (6:9.18-0ubuntu0.14.04.1) ...
Removing libavresample1:amd64 (6:9.18-0ubuntu0.14.04.1) ...
Removing libbasicusageenvironment0 (2014.01.13-1) ...
Removing libbind9-90 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Removing libboost-date-time1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-filesystem1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-locale1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-python1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-regex1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-signals1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing liborcus-0.6-0 (0.5.1-7) ...
Removing libboost-thread1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libboost-system1.54.0:amd64 (1.54.0-4ubuntu3.1) ...
Removing libcdr-0.0-0 (0.0.15-1ubuntu1) ...
Removing libcgmanager0:i386 (0.39-2ubuntu5) ...
Removing libcolorhug1:amd64 (1.0.6-1) ...
Removing libcrypt-passwdmd5-perl (1.3-10) ...
Removing libcuda1-349 (349.16-0ubuntu0~xedgers14.04.1) ...
Removing libdata-optlist-perl (0.109-1) ...
Removing libdbd-mysql-perl (4.033-1build2) ...
Removing libisccfg90 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libdns100 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libdolphinvcs5:amd64 (4:15.12.3-0ubuntu1) ...
Removing libdvbpsi8:amd64 (1.0.0-3) ...
Removing libebackend-1.2-7 (3.10.4-0ubuntu1.5) ...
Removing libegl1-mesa-drivers:amd64 (11.2.0-1ubuntu2.1) ...
Removing libelfg0:amd64 (0.8.13-5) ...
Removing libepub0 (0.2.2-4build1) ...
Removing libestools2.1:amd64 (1:2.1~release-6) ...
Removing libgcj14:amd64 (4.8.5-4ubuntu2) ...
Removing libgcrypt11-dev (1.5.4-3+really1.6.5-2) ...
Removing libgcrypt20-dev (1.6.5-2) ...
Removing libgdata13 (0.14.1-1) ...
Removing libglamor0:amd64 (0.6.0+git20140801.347ef4f0-0ubuntu0sarvatt~trusty) ...
Removing libglewmx1.10:amd64 (1.10.0-3) ...
Removing libgnome-bluetooth11 (3.8.2.1-0ubuntu4.2) ...
Removing libgnome-desktop-3-7 (3.8.4-0ubuntu3.2) ...
Removing libgnutlsxx27:amd64 (2.12.23-12ubuntu2.5) ...
Removing libgpg-error-dev (1.21-2ubuntu1) ...
Removing libgphoto2-dev:amd64 (2.5.9-3) ...
Removing libgphoto2-port10:amd64 (2.5.3.1-1ubuntu2.2) ...
Removing libgphoto2-port10:i386 (2.5.3.1-1ubuntu2.2) ...
Removing libgps20:amd64 (3.9-3) ...
Removing libgps22:amd64 (3.15-2build1) ...
Removing libgroupsock1 (2014.01.13-1) ...
Removing libicc2:amd64 (2.12+argyll1.5.1-5ubuntu1) ...
Removing libidl-common (0.8.14-0.2ubuntu4) ...
Removing libieee1284-3-dev (0.2.11-12) ...
Removing libimdi0:amd64 (1.5.1-5ubuntu1) ...
Removing libimobiledevice4:amd64 (1.1.5+git20140313.bafe6a9e-0ubuntu1.1) ...
Removing libisccc90 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libisc95 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libisl10:amd64 (0.12.2-1) ...
Removing libjson0:amd64 (0.11-4ubuntu2) ...
Removing libkf5balooengine5 (5.18.0-0ubuntu1.1) ...
Removing libkf5kcmutils-data (5.18.0-0ubuntu1) ...
Removing libkf5parts-data (5.18.0-0ubuntu1) ...
Removing libkgeomap-data (1.0~digikam3.5.0-0ubuntu10) ...
Removing liblinear1 (1.8+dfsg-1ubuntu1) ...
Removing liblivemedia23 (2014.01.13-1) ...
Removing liblmdb0:amd64 (0.9.17-3) ...
Removing libterm-ui-perl (0.46-1) ...
Removing liblog-message-simple-perl (0.10-2) ...
Removing liblog-message-perl (0.8-1) ...
Removing liblouis2:amd64 (2.5.3-2ubuntu1) ...
Removing liblwres90 (1:9.9.5.dfsg-3ubuntu0.8) ...
Removing libmagick++5:amd64 (8:6.7.7.10-6ubuntu3.1) ...
Removing libmagickcore5-extra:amd64 (8:6.7.7.10-6ubuntu3.1) ...
Removing libmagickwand5:amd64 (8:6.7.7.10-6ubuntu3.1) ...
Removing libmagickcore5:amd64 (8:6.7.7.10-6ubuntu3.1) ...
Removing libmbim-glib0:amd64 (1.6.0-2ubuntu0.1) ...
Removing libmikmod2:amd64 (3.1.16-1) ...
Removing libminiupnpc8 (1.6-3ubuntu2.14.04.2) ...
Removing libmodule-pluggable-perl (5.2-1) ...
Removing libuil4:amd64 (2.3.4-10) ...
Removing libmrm4:amd64 (2.3.4-10) ...
Removing libmspub-0.0-0 (0.0.6-1ubuntu2) ...
Removing libmusicbrainz5-0:amd64 (5.0.1-2) ...
Removing libmysqlclient18:amd64 (5.5.50-0ubuntu0.14.04.1) ...
Removing libnepomukcleaner4 (4:4.13.3-0ubuntu0.2) ...
Removing libnih-dbus1:i386 (1.0.3-4.3ubuntu1) ...
Removing libnih1:i386 (1.0.3-4.3ubuntu1) ...
Removing libpano13-2:amd64 (2.9.18+dfsg-6ubuntu2) ...
Removing libunityvoice1:amd64 (0.1+14.04.20140304-0ubuntu1) ...
Removing unity-voice-service:amd64 (0.1+14.04.20140304-0ubuntu1) ...
Removing libpocketsphinx1 (0.8.0+real-0ubuntu6) ...
Removing libpod-latex-perl (0.61-2) ...
Removing 'diversion of /usr/bin/pod2latex to /usr/bin/pod2latex.bundled by libpod-latex-perl'
Removing 'diversion of /usr/share/man/man1/pod2latex.1.gz to /usr/share/man/man1/pod2latex.bundled.1.gz by libpod-latex-perl'
Removing lsb-languages (4.1+Debian11ubuntu6.1) ...
Removing libpod-plainer-perl (1.04-1) ...
Removing libpoppler-private-dev:amd64 (0.41.0-0ubuntu1) ...
Removing libpoppler44:amd64 (0.24.5-2ubuntu4.4) ...
Removing libprocps3:amd64 (1:3.3.9-1ubuntu2.2) ...
Removing libprotoc8:amd64 (2.5.0-9ubuntu1) ...
Removing libprotobuf8:amd64 (2.5.0-9ubuntu1) ...
Removing libpth20:amd64 (2.0.7-20) ...
Removing libqapt3-runtime (3.0.2-0ubuntu1.1) ...
Removing libqapt3 (3.0.2-0ubuntu1.1) ...
Removing libqextserialport1:amd64 (1.2.0~rc1+git7-g3be3fbf-1) ...
Removing libqmi-glib0:amd64 (1.4.0-1) ...
Removing libqpdf13:amd64 (5.1.1-1) ...
Removing libqt5qml-graphicaleffects (5.5.1-1ubuntu1) ...
Removing libqt5sensors5:amd64 (5.5.1-1ubuntu2) ...
Removing libqt5webkit5-qmlwebkitplugin (5.5.1+dfsg-2ubuntu1) ...
Removing libqtlocation1:amd64 (1.2.0-3ubuntu5) ...
Removing libqtscript4-gui:amd64 (0.2.0-1) ...
Removing libqtscript4-xml:amd64 (0.2.0-1) ...
Removing libqtscript4-network:amd64 (0.2.0-1) ...
Removing libqtscript4-uitools:amd64 (0.2.0-1) ...
Removing libquazip0:amd64 (0.6.2-0ubuntu1) ...
Removing libraw9:amd64 (0.15.4-1) ...
Removing librhythmbox-core8 (3.0.2-0ubuntu2) ...
Removing librpmsign1 (4.11.1-3ubuntu0.1) ...
Removing libstk0c2a:amd64 (4.4.4-4) ...
Removing librtaudio4:amd64 (4.0.12~ds0-1ubuntu1) ...
Removing librtmidi1:amd64 (2.0.1~ds0-3ubuntu1) ...
Removing libservlet3.0-java (7.0.68-1ubuntu0.1) ...
Removing libshp1:amd64 (1.2.10-7) ...
Removing libshp2:amd64 (1.3.0-5) ...
Removing libsphinxbase1 (0.8-0ubuntu10) ...
Removing libspice-server1:amd64 (0.12.6-4ubuntu0.1) ...
Removing libsystemd-daemon0:amd64 (204-5ubuntu20.19) ...
Removing libsystemd-journal0:amd64 (204-5ubuntu20.19) ...
Removing libsystemd-login0:amd64 (204-5ubuntu20.19) ...
Removing libtagc0:amd64 (1.9.1-2.4ubuntu1) ...
Removing libtext-soundex-perl (3.4-1build3) ...
Removing libthumbnailer0:amd64 (1.1+14.04.20150205-0ubuntu1) ...
Removing libtinyxml2-0.0.0:amd64 (0~git20120518.1.a2ae54e-1) ...
Removing libusageenvironment1 (2014.01.13-1) ...
Removing libusb-1.0-0-dev:amd64 (2:1.0.20-1) ...
Removing libusb-1.0-doc (2:1.0.20-1) ...
Removing libusbmuxd2 (1.0.8-2ubuntu1) ...
Removing libvisio-0.0-0 (0.0.31-1ubuntu2) ...
Removing libvpx1:i386 (1.3.0-2) ...
Removing libwebkit2gtk-3.0-25:amd64 (2.4.11-0ubuntu0.1) ...
Removing libwlocate0 (0.0git20130108-0ubuntu1) ...
Removing libwps-0.2-2 (0.2.9-2ubuntu1) ...
Removing libwpg-0.2-2 (0.2.2-1ubuntu1) ...
Removing libwpd-0.9-9 (0.9.9-1) ...
Removing libxcb-util0:amd64 (0.3.8-2ubuntu1) ...
Removing libxt-dev:amd64 (1:1.1.5-0ubuntu1) ...
Removing libxtables10 (1.4.21-1ubuntu1) ...
Removing libzip2 (0.10.1-1.2) ...
Removing libzthread-2.3-2:amd64 (2.3.2-7.2) ...
Removing lsb-cxx (4.1+Debian11ubuntu6.1) ...
Removing lsb-desktop (4.1+Debian11ubuntu6.1) ...
Removing lsb-graphics (4.1+Debian11ubuntu6.1) ...
Removing lsb-multimedia (4.1+Debian11ubuntu6.1) ...
Removing marble-data (4:15.12.3-0ubuntu2) ...
Removing nepomuk-core-data (4:4.13.3-0ubuntu0.2) ...
Removing python-matplotlib (1.5.1-1ubuntu1) ...
Removing python-cycler (0.9.0-1) ...
Removing python-dateutil (2.4.2-1) ...
Removing python-dbus-dev (1.2.0-3) ...
Removing python-gst-1.0 (1.6.2-1build1) ...
Removing python-tz (2014.10~dfsg1-0ubuntu2) ...
Removing qtdeclarative5-localstorage-plugin:amd64 (5.5.1-2ubuntu6) ...
Removing qml-module-qtquick-localstorage:amd64 (5.5.1-2ubuntu6) ...
Removing qtdeclarative5-dialogs-plugin:amd64 (5.5.1-1ubuntu1) ...
Removing qtdeclarative5-privatewidgets-plugin:amd64 (5.5.1-1ubuntu1) ...
Removing qtdeclarative5-qtfeedback-plugin:amd64 (5.0~git20130529-0ubuntu13) ...
Removing qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets (0.23+14.04.20140428-0ubuntu1) ...
Removing qtdeclarative5-window-plugin:amd64 (5.5.1-2ubuntu6) ...
Removing ruby-vte (2.1.0-1) ...
Removing ruby-vte3 (2.1.0-1) ...
Removing sphinx-voxforge-hmm-en (0.1.1~daily20130301-0ubuntu1) ...
Removing sphinx-voxforge-lm-en (0.1.1~daily20130301-0ubuntu1) ...
Removing unity-scope-audacious (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-clementine (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-gmusicbrowser (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-gourmet (0.1+13.10.20130723-0ubuntu1) ...
Removing unity-scope-guayadeque (0.1+13.10.20130927.1-0ubuntu1) ...
Removing unity-scope-musique (0.1+13.10.20130723-0ubuntu1) ...
Removing libedataserver-1.2-18 (3.10.4-0ubuntu1.5) ...
Removing libcamel-1.2-45 (3.10.4-0ubuntu1.5) ...
Removing libqtscript4-core:amd64 (0.2.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:i386 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for tex-common (6.04) ...
Running mktexlsr. This may take some time... done.
Processing triggers for doc-base (0.10.7) ...
Processing 4 removed doc-base files, 2 added doc-base files...
Error while merging /usr/share/doc-base/kino-en with /usr/share/doc-base/kino-fr: format html already defined.
Registering documents with scrollkeeper...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Setting up cron (3.0pl1-128ubuntu2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match cron Default-Stop values (none)
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cron (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up initscripts (2.88dsf-59.3ubuntu2) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: warning: script 'virtuoso-nepomuk' missing LSB tags and overrides
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of procps:
 procps depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package procps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools-core:
 initramfs-tools-core depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package initramfs-tools-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-core (= 0.122ubuntu8.1); however:
  Package initramfs-tools-core is not configured yet.

dpkg: error processing package initramfs-tools (--configure)No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                      :
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of brltty:
 brltty depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.

dpkg: error processing package brltty (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.

dpkg: error processing package bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools | dracut; however:
  Package initramfs-tools is not configured yet.
  Package dracut is not installed.

dpkg: error processing package plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.

dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
Setting up asunder (2.8-3) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of cmake:
 cmake depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cmake (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up grub-common (2.02~beta2-36ubuntu3.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package winbind is not configured yet.

dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
 libpam-winbind:amd64 depends on winbind (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package winbind is not configured yet.

dpkg: error processing package libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up libsratom-0-0:amd64 (0.4.6~dfsg0-1) ...
Setting up libqtdbus4:i386 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqtdbus4:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-network:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-network:i386 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-script:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-script:i386 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-xmlpatterns:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-xmlpatterns:i386 (4:4.8.7+dfsg-5ubuntu2) ...
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lightdm:
 lightdm depends on plymouth (>= 0.8.8-0ubuntu18); however:
  Package plymouth is not configured yet.

dpkg: error processing package lightdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server-5.7:
 mysql-server-5.7 depends on apparmor (>= 2.10); however:
  Package apparmor is not configured yet.
 mysql-server-5.7 depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package mysql-server-5.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up alsa-utils (1.1.0-0ubuntu5) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package alsa-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on udev (>= 204-0ubuntu4~); however:
  Package udev is not configured yet.
 ubuntu-drivers-common depends on alsa-utils; however:
  Package alsa-utils is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up whoopsie (0.2.52.1) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up 0install (2.10-2) ...
Setting up zeroinstall-injector (2.10-2) ...
Setting up gcc (4:5.3.1-1ubuntu1) ...
Setting up ghc (7.10.3-7) ...
update-alternatives: using /usr/bin/runghc to provide /usr/bin/runhaskell (runhaskell) in auto mode
update-alternatives: using /usr/bin/ghc to provide /usr/bin/haskell-compiler (haskell-compiler) in auto mode
dpkg: dependency problems prevent configuration of keyboard-configuration:
 keyboard-configuration depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package keyboard-configuration (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.
 console-setup depends on initramfs-tools (>= 0.85eubuntu12) | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kbd:
 kbd depends on console-setup | console-setup-mini; however:
  Package console-setup is not configured yet.
  Package console-setup-mini is not installed.

dpkg: error processing package kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup-linux:No apport report written because MaxReports is reached already

 console-setup-linux depends on kbd (>= 1.15-1ubuntu3); however:
  Package kbd is not configured yet.
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up debconf-i18n (1.5.58ubuntu1) ...
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 ubuntu-minimal depends on kbd; however:
  Package kbd is not configured yet.
 ubuntu-minimal depends on procps; however:
  Package procps is not configured yet.
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up bind9-host (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up dnsutils (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up irqbalance (1.1.0-2ubuntu1) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth (= 0.9.2-3ubuntu13.1); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cron; however:
  Package cron is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up gstreamer1.0-nice:amd64 (0.1.13-0ubuntu2) ...
Setting up libfarstream-0.2-5:amd64 (0.2.7-0ubuntu1) ...
Setting up libtelepathy-farstream3:amd64 (0.6.2-1build1) ...
Setting up empathy (3.12.11-0ubuntu3) ...
Setting up mcp-account-manager-uoa (3.12.11-0ubuntu3) ...
Setting up libaccount-plugin-generic-oauth (0.12+16.04.20160126-0ubuntu1) ...
Setting up account-plugin-facebook (0.12+16.04.20160126-0ubuntu1) ...
Setting up account-plugin-flickr (0.12+16.04.20160126-0ubuntu1) ...
Setting up account-plugin-google (0.12+16.04.20160126-0ubuntu1) ...
Setting up telepathy-gabble (0.18.3-2build1) ...
Setting up account-plugin-jabber (3.12.11-0ubuntu3) ...
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on udev (>= 143); however:
  Package udev is not configured yet.

dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio (= 1:8.0-0ubuntu3); however:
  Package pulseaudio is not configured yet.
 pulseaudio-module-bluetooth depends on bluez (>= 5.23); however:
  Package bluez is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
 pulseaudio-esound-compat depends on pulseaudio (= 1:8.0-0ubuntu3); however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured
Setting up avahi-daemon (0.6.32~rc+dfsg-1ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              Installing new version of config file /etc/avahi/avahi-daemon.conf ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package avahi-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of telepathy-salut:
 telepathy-salut depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package telepathy-salut (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of account-plugin-salut:
 account-plugin-salut depends on telepathy-salut; however:No apport report written because MaxReports is reached already

  Package telepathy-salut is not configured yet.

dpkg: error processing package account-plugin-salut (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up activity-log-manager (0.9.7-0ubuntu23) ...
Setting up activity-log-manager-control-center (0.9.7-0ubuntu23) ...
Setting up gettext (0.19.7-2ubuntu3) ...
Setting up intltool-debian (0.35.0+20060710.4) ...
Setting up po-debconf (1.0.19) ...
dpkg: dependency problems prevent configuration of alsa-base:
 alsa-base depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package alsa-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor-utils:
 apparmor-utils depends on apparmor (>= 2.6.1-4ubuntu1); however:
  Package apparmor is not configured yet.

dpkg: error processing package apparmor-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up liblilv-0-0 (0.22.0~dfsg0-1) ...
dpkg: dependency problems prevent configuration of avahi-utils:
 avahi-utils depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up qdbus (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-dbus:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up libqt4-dbus:i386 (4:4.8.7+dfsg-5ubuntu2) ...
Setting up binfmt-support (2.1.6-1) ...
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package binfmt-support (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up bleachbit (1.10-1) ...
Setting up blt (2.5.3+dfsg-3) ...
dpkg: dependency problems prevent configuration of bluetooth:
 bluetooth depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 2.1.3-4); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 2.1.3-4); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 2.1.3-4); however:
  Package cups-daemon is not configured yet.
 cups depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 cron
 initscripts
 procps
 udev
 initramfs-tools-core
 initramfs-tools
 brltty
 bluez
 plymouth
 mountall
 upstart
 cmake
 cups-daemon
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 apparmor
 lightdm
 mysql-server-5.7
 alsa-utils
 ubuntu-drivers-common
 whoopsie
 keyboard-configuration
 console-setup
 kbd
 console-setup-linux
 ubuntu-minimal
 irqbalance
 plymouth-theme-ubuntu-text
 ubuntu-standard
 pulseaudio
 pulseaudio-module-bluetooth
 pulseaudio-esound-compat
 avahi-daemon
 telepathy-salut
 account-plugin-salut
 alsa-base
 apparmor-utils
 apport-gtk
 software-properties-gtk
 apturl
 avahi-utils
 binfmt-support
 bluetooth
 cups-core-drivers
 cups
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` What now?

---

### Post by Bucky Ball on 2016-08-07
```
 sudo apt-get update
sudo apt-get dist-upgrade
```

Try that.

---

### Post by cscj01 on 2016-08-07
```
sudo apt-get update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Hit:3 http://archive.canonical.com xenial InRelease                            
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Hit:5 http://archive.ubuntu.com/ubuntu xenial-backports InRelease              
Fetched 94.5 kB in 0s (138 kB/s)                                               
Reading package lists... Done

``````
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  jhead
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
957 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up cron (3.0pl1-128ubuntu2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match cron Default-Stop values (none)
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cron (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up initscripts (2.88dsf-59.3ubuntu2) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: warning: script 'virtuoso-nepomuk' missing LSB tags and overrides
insserv: warning: script 'screen-cleanup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `screen-cleanup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `screen-cleanup'
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of procps:
 procps depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package procps (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of initramfs-tools-core:
 initramfs-tools-core depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package initramfs-tools-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-core (= 0.122ubuntu8.1); however:
  Package initramfs-tools-core is not configured yet.

dpkg: error processing package initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of brltty:
 brltty depends on initramfs-tools (>= 0.40ubuntu30); however:
  Package initramfs-tools is not configured yet.

dpkg: error processing package brltty (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bluez:
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.

dpkg: error processing package bluez (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools | dracut; however:
  Package initramfs-tools is not configured yet.
  Package dracut is not installed.

dpkg: error processing package plymouth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mountall:
 mountall depends on udev; however:
  Package udev is not configured yet.
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.

dpkg: error processing package mountall (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of upstart:
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.

dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cmake:
 cmake depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cmake (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up grub-common (2.02~beta2-36ubuntu3.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-36ubuntu3.2); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-36ubuntu3.2); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package samba is not configured yet.

dpkg: error processing package winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package winbind is not configured yet.

dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-winbind:amd64:
No apport report written because MaxReports is reached already
                                                               libpam-winbind:amd64 depends on winbind (= 2:4.3.9+dfsg-0ubuntu0.16.04.2); however:
  Package winbind is not configured yet.

dpkg: error processing package libpam-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on initramfs-tools | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.

dpkg: error processing package apparmor (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of lightdm:
 lightdm depends on plymouth (>= 0.8.8-0ubuntu18); however:
  Package plymouth is not configured yet.

dpkg: error processing package lightdm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server-5.7:
 mysql-server-5.7 depends on apparmor (>= 2.10); however:
  Package apparmor is not configured yet.
 mysql-server-5.7 depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package mysql-server-5.7 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up alsa-utils (1.1.0-0ubuntu5) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package alsa-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on udev (>= 204-0ubuntu4~); however:
  Package udev is not configured yet.
 ubuntu-drivers-common depends on alsa-utils; however:
  Package alsa-utils is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leaving unconfigured
Setting up whoopsie (0.2.52.1) ...
No apport report written because MaxReports is reached already
                                                              insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of keyboard-configuration:
 keyboard-configuration depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing package keyboard-configuration (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of console-setup:
 console-setup depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.
 console-setup depends on initramfs-tools (>= 0.85eubuntu12) | linux-initramfs-tool; however:
  Package initramfs-tools is not configured yet.
  Package linux-initramfs-tool is not installed.
  Package initramfs-tools which provides linux-initramfs-tool is not configured yet.

dpkg: error processing package console-setup (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kbd:
 kbd depends on console-setup | console-setup-mini; however:
  Package console-setup is not configured yet.
  Package console-setup-mini is not installed.

dpkg: error processing package kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of console-setup-linux:No apport report written because MaxReports is reached already

 console-setup-linux depends on kbd (>= 1.15-1ubuntu3); however:
  Package kbd is not configured yet.
 console-setup-linux depends on keyboard-configuration (= 1.108ubuntu15.2); however:
  Package keyboard-configuration is not configured yet.

dpkg: error processing package console-setup-linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on console-setup; however:
  Package console-setup is not configured yet.
 ubuntu-minimal depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
 ubuntu-minimal depends on kbd; however:
  Package kbd is not configured yet.
 ubuntu-minimal depends on procps; however:
  Package procps is not configured yet.
 ubuntu-minimal depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up irqbalance (1.1.0-2ubuntu1) ...
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package irqbalance (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth (= 0.9.2-3ubuntu13.1); however:
  Package plymouth is not configured yet.

dpkg: error processing package plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cron; however:
  Package cron is not configured yet.

dpkg: error processing package ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on udev (>= 143); however:
  Package udev is not configured yet.

dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio (= 1:8.0-0ubuntu3); however:
  Package pulseaudio is not configured yet.
 pulseaudio-module-bluetooth depends on bluez (>= 5.23); however:No apport report written because MaxReports is reached already

  Package bluez is not configured yet.

dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
 pulseaudio-esound-compat depends on pulseaudio (= 1:8.0-0ubuntu3); however:
  Package pulseaudio is not configured yet.

dpkg: error processing package pulseaudio-esound-compat (--configure):
 dependency problems - leaving unconfigured
Setting up avahi-daemon (0.6.32~rc+dfsg-1ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package avahi-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of telepathy-salut:
 telepathy-salut depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package telepathy-salut (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of account-plugin-salut:
 account-plugin-salut depends on telepathy-salut; however:
  Package telepathy-salut is not configured yet.

dpkg: error processing package account-plugin-salut (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of alsa-base:
 alsa-base depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package alsa-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apparmor-utils:
 apparmor-utils depends on apparmor (>= 2.6.1-4ubuntu1); however:
  Package apparmor is not configured yet.

dpkg: error processing package apparmor-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of avahi-utils:
 avahi-utils depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up binfmt-support (2.1.6-1) ...
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `binfmt-support'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `binfmt-support'
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package binfmt-support (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of bluetooth:
 bluetooth depends on bluez; however:
  Package bluez is not configured yet.

dpkg: error processing package bluetooth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 2.1.3-4); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 2.1.3-4); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 2.1.3-4); however:
  Package cups-daemon is not configured yet.
 cups depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cron
 initscripts
 procps
 udev
 initramfs-tools-core
 initramfs-tools
 brltty
 bluez
 plymouth
 mountall
 upstart
 cmake
 cups-daemon
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 samba
 winbind
 libnss-winbind:amd64
 libpam-winbind:amd64
 apparmor
 lightdm
 mysql-server-5.7
 alsa-utils
 ubuntu-drivers-common
 whoopsie
 keyboard-configuration
 console-setup
 kbd
 console-setup-linux
 ubuntu-minimal
 irqbalance
 plymouth-theme-ubuntu-text
 ubuntu-standard
 pulseaudio
 pulseaudio-module-bluetooth
 pulseaudio-esound-compat
 avahi-daemon
 telepathy-salut
 account-plugin-salut
 alsa-base
 apparmor-utils
 apport-gtk
 software-properties-gtk
 apturl
 avahi-utils
 binfmt-support
 bluetooth
 cups-core-drivers
 cups
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```It appears that there are many failures because of dependencies.

I tried to run synaptic from a terminal, and here the messages I received while using Synaptic to try to "Fix Broken Packages" and to Look at Sources.```
sudo synaptic
/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 155, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 654, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 246, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
dbus.exceptions.UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: Reload is not a valid method of interface com.ubuntu.SoftwareProperties

/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 155, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 654, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 246, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
dbus.exceptions.UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: Reload is not a valid method of interface com.ubuntu.SoftwareProperties

/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 155, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 654, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 246, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
dbus.exceptions.UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: Reload is not a valid method of interface com.ubuntu.SoftwareProperties

/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:40: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, Gio, GLib
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 155, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 654, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/usr/lib/python3/dist-packages/dbus/service.py", line 246, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
dbus.exceptions.UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: Reload is not a valid method of interface com.ubuntu.SoftwareProperties

/usr/bin/deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

Exception in RPackageLister::xapianSearch():The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
Exception in RPackageLister::xapianSearch():The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
Exception in RPackageLister::xapianSearch():Document 3871 not found.
Exception in RPackageLister::xapianSearch():Document 3871 not found.
Exception in RPackageLister::xapianSearch():The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
Exception in RPackageLister::xapianSearch():Document 3134 not found.
Exception in RPackageLister::xapianSearch():Document 3134 not found.

```

Well, I think I'm going to try to reboot this system and see what happens.  Assuming, as I do, that things won't work, I'll restore my backup.  I can't wait around for someone who understands why this thing has gone so wrong to see this thread and tell me how to fix this mess.

---

### Post by umrashrf89 on 2016-08-07
> **cscj01 said:**
> Well, I think I'm going to try to reboot this system and see what happens.  Assuming, as I do, that things won't work, I'll restore my backup.  I can't wait around for someone who understands why this thing has gone so wrong to see this thread and tell me how to fix this mess.

What do you see when you run ```
[COLOR=#000000][FONT=&amp]sudo dpkg --configure -a[/FONT][/COLOR]
```

---

### Post by Bucky Ball on 2016-08-07
I advised you should reboot after the commands in post #2. ;)

These upgrades can be problematic and often end up in a reinstall when they do. Sure you have backups, though.

---

### Post by cscj01 on 2016-08-07
Well, I was correct.  When I tried to reboot, I got nothing but a black screen.  I could not get out of it without a hard reboot.  Same thing.  So I restored by backup, and I am now back on 14.04.5.  It amazes me that the upgrade process is so fraught with error.  There was not a message that allowed me to recover at any point.  The script just ran until things were so out of whack that it just said, "I give up.  You're on your own, sucker."  I worked in IT for 40 years with mainframes, mid-range systems, distributed processing systems, advanced workstations, and min-processor systems.  Never did I install an upgrade that did not give you a chance to recover or back out at some point.  In fact, I have gone through a number of upgrades with Ubuntu starting with 8.04.  This is the worst of all.  Let's hope the folks at Ubuntu get their act together soon.

---

### Post by Bucky Ball on 2016-08-07
Did you do a full update/upgrade, as in the commands I gave previously, prior to upgrading? Did you disable any PPAs you have added manually? Did you attempt to get the machine back to a 'vanilla' state prior to upgrading (i.e. disable any third-party drivers you have installed manually)?

These are usually the causes of a bad upgrade, particularly the omission of an update prior to the release upgrade.

---

### Post by cscj01 on 2016-08-08
> **Bucky Ball said:**
> Did you do a full update/upgrade, as in the commands I gave previously, prior to upgrading? Did you disable any PPAs you have added manually? Did you attempt to get the machine back to a 'vanilla' state prior to upgrading (i.e. disable any third-party drivers you have installed manually)?

These are usually the causes of a bad upgrade, particularly the omission of an update prior to the release upgrade.

Yes, I did do```
sudo apt-get update
sudo apt-get upgrade
```before beginning the upgrade process.  I did disable the PPA's, although the upgrade script has always stated they will disabled them automatically.  I did not disable my Nvidia driver, because the screen gets screwed up when I go with any of the system drivers.  However, I have never had to disable the Nvidia driver in the past.  The ones I use seem to be available with the system, and I select it rather than install it manually.

One point I will note is that I did not do the reboot after the two commands```
sudo apt-get update
sudo apt-get upgrade
```because the system was so screwed up by the time I had posted, and I knew it would not boot if I did not clear up the dependencies issue.

---

### Post by stephenbbb on 2016-08-09
Same issues as poster. this is the worst upgrade in Ubuntu history and the silence from Canonical is scary. may be time to switch to a better supported version of Linux ??

---

### Post by philo4 on 2016-08-09
Hi Bucky Ball,
Just seen you helped cscj01 who has also faced a challenge with upgrading from 14.04 to 16.04.
Anything tried so far with or without Live USB downloaded from the internet has not shown any real satisfaction.
As a result, this led me to carry out a lot of search online, before realizing so many people have encountered electronic crisis and paralysis because of 16.04 LTS.
A call to Canonical in London did not bring any solution either.
These have been 5 days without access to my data...
Any further suggestion?
Many thanks in advance
Philo

---

