---
title: "sudo aptitude upgrade - strange response!"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by tchoklat on 2006-12-11
please note the response to this command in Konsole;


[COLOR=Red]sudo aptitude upgrade
Password: ******
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  artsbuilder atlantik atlantikdesigner comerr-dev gettext-kde hspell juk
  kaboodle kaddressbook-plugins kate-plugins kdat kdeaddons
  kdeaddons-kfile-plugins kdeadmin kdeartwork kdeartwork-emoticons
  kdeartwork-misc kdeartwork-style kdeartwork-theme-icon
  kdeartwork-theme-window kdegames-card-data kdelibs4-dev kdemultimedia
  kdemultimedia-dev kdemultimedia-kappfinder-data kdesdk-scripts
  kdewallpapers kicker-applets kmid knewsticker-scripts kpackage kpat
  kpoker krec ksig ksysv kuser libacl1-dev libart-2.0-dev
  libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine
  libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libaudio-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-qt3-dev
  libbz2-dev libconvert-binhex-perl libcupsys2-dev libdb4.3++c2
  libdbus-1-dev libesd0-dev libfinance-quote-perl libgcrypt11-dev
  libglu1-mesa-dev libgnutls-dev libgpg-error-dev libhtml-tableextract-perl
  libidn11-dev libio-stringy-perl libjasper-1.701-dev libjpeg62-dev
  libkadm55 libkrb5-dev liblcms1-dev liblua50-dev liblualib50-dev
  liblzo-dev libmime-perl libmng-dev libnews-nntpclient-perl libogg-dev
  libopencdk8-dev libopenexr-dev libpcre3-dev libpcrecpp0 libpopt-dev
  libqt3-headers libqt3-mt-dev libsasl2-dev libssl-dev libtasn1-3-dev
  libtidy-0.99-0 libtiff4-dev libtiffxx0c2 libtunepimp-bin libvorbis-dev
  libxml2-dev libxmu-dev libxmu-headers libxslt1-dev lskat lua50 mpeglib
  noatun noatun-plugins qt3-dev-tools secpolicy tidy
0 packages upgraded, 0 newly installed, 105 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 150MB will be freed.
Do you want to continue? [Y/n/?]  [/COLOR]

Why does it want to remove all these processes?

What are they and should I say yes or no?

I run Kubuntu Edgy.

It also happens when I try to install a program.
[COLOR=Red]
tony@tony:~$ sudo aptitude install ubuntu
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
Couldn't find package "ubuntu", and more than 40
packages contain "ubuntu" in their name.
The following packages are unused and will be REMOVED:
  artsbuilder atlantik atlantikdesigner comerr-dev gettext-kde hspell juk
  kaboodle kaddressbook-plugins kate-plugins kdat kdeaddons
  kdeaddons-kfile-plugins kdeadmin kdeartwork kdeartwork-emoticons
  kdeartwork-misc kdeartwork-style kdeartwork-theme-icon
  kdeartwork-theme-window kdegames-card-data kdelibs4-dev kdemultimedia
  kdemultimedia-dev kdemultimedia-kappfinder-data kdesdk-scripts
  kdewallpapers kicker-applets kmid knewsticker-scripts kpackage kpat
  kpoker krec ksig ksysv kuser libacl1-dev libart-2.0-dev
  libarts1-audiofile libarts1-dev libarts1-mpeglib libarts1-xine
  libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libaudio-dev
  libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-qt3-dev
  libbz2-dev libconvert-binhex-perl libcupsys2-dev libdb4.3++c2
  libdbus-1-dev libesd0-dev libfinance-quote-perl libgcrypt11-dev
  libglu1-mesa-dev libgnutls-dev libgpg-error-dev libhtml-tableextract-perl
  libidn11-dev libio-stringy-perl libjasper-1.701-dev libjpeg62-dev
  libkadm55 libkrb5-dev liblcms1-dev liblua50-dev liblualib50-dev
  liblzo-dev libmime-perl libmng-dev libnews-nntpclient-perl libogg-dev
  libopencdk8-dev libopenexr-dev libpcre3-dev libpcrecpp0 libpopt-dev
  libqt3-headers libqt3-mt-dev libsasl2-dev libssl-dev libtasn1-3-dev
  libtidy-0.99-0 libtiff4-dev libtiffxx0c2 libtunepimp-bin libvorbis-dev
  libxml2-dev libxmu-dev libxmu-headers libxslt1-dev lskat lua50 mpeglib
  noatun noatun-plugins qt3-dev-tools secpolicy tidy
0 packages upgraded, 0 newly instaled, 105 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 150MB will be freed.
Do you want to continue? [Y/n/?] [/COLOR]  



any help appreciated,

tchoklat

---

### Post by aysiu on 2006-12-11
Sometimes *aptitude* tries too hard to be smart and ends up dumb. I'd use *apt-get* in this case.

---

### Post by tchoklat on 2006-12-11
thanks dude apt-get did not try to rid me of 150mb of files !

tchoklat

---

### Post by studiesrule on 2006-12-11
I think aptitude recognised that the those files were not being used (as are dependecies of programs you've removed), and is trying get rid of them. If you have no problems with space, just leave them be.

Aptitude does not have Super Cow Powers
APT has Super Cow Powers

---

