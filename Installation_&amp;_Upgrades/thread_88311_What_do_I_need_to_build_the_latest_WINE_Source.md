---
title: "What do I need to build the latest WINE Source?"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by jeffreyvergara.NET on 2005-11-09
Hello, Im trying to build the latest WINE from source, but Im having trouble with it. I want to build it from source because I want to try something that a certain online game might work.

here's my souces.list
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


I run this command: apt-get build-dep wine, but I get this:
>   debconf-utils debhelper docbook docbook-dsssl docbook-to-man docbook-utils
  docbook-xsl fontforge gettext html2text intltool-debian jadetex libarts1-dev
  libartsc0-dev libasound2-dev libaudio-dev libaudiofile-dev libcapi20-3
  libcapi20-dev libcupsys2-dev libesd0-dev libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev libglib1.2-dev
  libglib2.0-dev libglu1-mesa-dev libgnutls11-dev libgpg-error-dev
  libicu28-dev libicu28c2 libjack0.80.0-dev libjpeg-mmx-dev libjpeg62-dev
  liblcms1-dev libmng-dev libncurses5-dev libogg-dev libopencdk8-dev libosp4
  libostyle1c2 libpng12-dev libqt3-headers libqt3-mt-dev libsgmls-perl
  libsp1c2 libssl-dev libt1-5 libtasn1-2-dev libungif4-dev libvorbis-dev
  libwww-ssl0 libxcursor-dev libxft-dev libxinerama-dev libxrender-dev
  nvidia-glx nvidia-glx-dev openjade po-debconf qt3-dev-tools sgmlspl sp
  tetex-base tetex-bin tetex-extra texinfo x11proto-gl-dev x11proto-render-dev
  x11proto-xinerama-dev


I just installed build-essentials, what other things/commands should I do?

thanks

---

