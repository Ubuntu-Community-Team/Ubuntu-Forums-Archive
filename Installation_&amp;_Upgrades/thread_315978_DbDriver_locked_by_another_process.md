---
title: "DbDriver locked by another process"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by p2cd3 on 2006-12-10
When I use apt-get I get this error message:

root@jack-desktop:~# apt-get install postgresql
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev libsm-dev libconvert-binhex-perl krec libattr1-dev ksig kdelibs4-dev knewsticker-scripts artsbuilder libice-dev ktip libaspell-dev libtunepimp-bin
  kdemultimedia-dev x11proto-xext-dev libtasn1-3-dev libaudiofile-dev libaudio-dev x11proto-kb-dev libglib2.0-dev libgpg-error-dev kpackage kdebase x11proto-xinerama-dev
  comerr-dev atlantikdesigner libpcre3-dev libopencdk8-dev x11proto-render-dev libgcrypt11-dev kpager liblualib50-dev libkdegames1 kde-core libxi-dev libxmu-headers
  libxrender-dev libfinance-quote-perl kdemultimedia-kappfinder-data mesa-common-dev libxdmcp-dev libkrb5-dev qt3-dev-tools libsasl2-dev libavahi-client-dev libogg-dev
  libjasper-1.701-dev noatun-plugins libpng12-dev mpeglib kicker-applets libfontconfig1-dev libpcrecpp0 xtrans-dev atlantik liblua50-dev tidy libtidy-0.99-0 x11proto-core-dev
  libxcursor-dev lua50 libavahi-qt3-dev libdb4.3++c2 libacl1-dev libglu1-mesa-dev libgnutls-dev libqt3-mt-dev ksysv x11proto-randr-dev hspell libio-stringy-perl kuser
  libdbus-1-dev libxslt1-dev libhtml-tableextract-perl libssl-dev libxt-dev libxmu-dev libxext-dev libjpeg62-dev juk noatun zlib1g-dev libarts1-mpeglib kaddressbook-plugins
  libxml2-dev x11proto-input-dev libtiff4-dev libfreetype6-dev libart-2.0-dev libesd0-dev x11proto-fixes-dev libxau-dev kaboodle liblzo-dev libmime-perl libqt3-headers
  libasound2-dev kdeartwork-theme-window libtiffxx0c2 libgl1-mesa-dev liblcms1-dev libxrandr-dev libkadm55 libexpat1-dev libarts1-audiofile libxft-dev libx11-dev kdelibs
  libxml2-utils kappfinder libartsc0-dev libopenexr-dev kdat libxfixes-dev libmng-dev secpolicy libavahi-common-dev libxinerama-dev kdesdk-scripts libcupsys2-dev libvorbis-dev
  kate-plugins kdeaddons-kfile-plugins gettext-kde libarts1-xine libidn11-dev libbz2-dev kmid libarts1-dev libnews-nntpclient-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postgresql-7.4 postgresql-client postgresql-common
Recommended packages:
  postgresql-plpython-7.4 postgresql-plperl-7.4 postgresql-pltcl-7.4
The following NEW packages will be installed:
  postgresql postgresql-7.4 postgresql-client postgresql-common
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/3420kB of archives.
After unpacking 9138kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process
(Reading database ... 99578 files and directories currently installed.)
Unpacking postgresql-common (from .../postgresql-common_62_all.deb) ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/postgresql-common_62_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Selecting previously deselected package postgresql-7.4.
Unpacking postgresql-7.4 (from .../postgresql-7.4_1%3a7.4.13-4_i386.deb) ...
Selecting previously deselected package postgresql-client.
Unpacking postgresql-client (from .../postgresql-client_7.5.21_all.deb) ...
Selecting previously deselected package postgresql.
Unpacking postgresql (from .../postgresql_7.5.21_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/postgresql-common_62_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I checked ps &  no process related to package managers are running

Why is DbDriver acting up?

---

