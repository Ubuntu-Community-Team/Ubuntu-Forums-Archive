---
title: "apt-get dist-upgrade wants to reinstall same versions just installed"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by sdalley on 2006-06-06
System: vanilla Athlon with ATA disks, nvidia FX5200 etc. Breezy had been working fine. Latest breezy updates installed via the autoupdate notifier.

What I did: Downloaded ubuntu 6.06 alternate-i686 cdrom image, created cd, added to repository list with apt-cdrom. Did apt-get dist-upgrade and all appeared OK, altho needed apt-get install nvidia-glx to get my nvidia X desktop working again. Purged repository to only official entries, changing all "breezy" to "dapper" Rebooted fine.

What went wrong:
Thought I'd do apt-get update; apt-get dist-upgrade -s to see I was now up to date, since I'd just upgraded from the cdrom, but *100s* of pkgs showed for update. Went back and commented out everything in sources.list but the cdrom, did update and dist-upgrade, which installed a *few* more pkgs such as cups, from cdrom. Uncommented ubuntu.org repositories again - back to hundreds.

My current sources.list is:
#---------schnipp----------------
## OFFICIALLY SUPPORTED REPOSITORIES

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted


## COMMUNITY SUPPORTED REPOSITORIES

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse


## BACKPORTS

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
#----------------schnapp--------------------

(selected chunks of output:>>>>>>>>>>>>>>>>>>>
root@centaur:~ # apt-get dist-upgrade -s # to show what WOULD be installed:
Reading package lists...
Building dependency tree...
The following packages will be REMOVED
  akode k3b k3blibs kaffeine-gstreamer kdelibs4c2 kuickshow libarts1c2
  libkcal2a libkdepim1 libkleopatra0a libmimelib1a libmusicbrainz4c2 libntfs5
  libopenexr2c2 libsmpeg0c2 libtag1c2 libtunepimp2c2 sanekonsole
The following NEW packages will be installed
  gsfonts-x11 gstreamer0.10-plugins-good irssi kaffeine-xine kdelibs4c2a
  kdepim-kresources kdnssd kfaxview krita-data ksplash-engine-moodin kwin
....
The following packages have been kept back:
  gnome-session kubuntu-live linux-doc rhythmbox
The following packages will be upgraded:
  akregator amarok amarok-arts apache apache-common app-install-data ark arts
  artsbuilder audacity bogofilter bogofilter-bdb bogofilter-common dash
  dcoprss desktop-base dirmngr dvgrab emacs-goodies-el emacsen-common ethereal
  ethereal-common fetchmail fftw3 file-roller flashplugin-nonfree
  foomatic-db-gimp-print fortunes frozen-bubble frozen-bubble-data
  gcc-3.4-base gedit-common gimp-help-common gimp-help-en gnome-app-install
  gnome-media gnupg-agent gnupg2 gpgsm gstreamer0.8-alsa
  gstreamer0.8-audiofile gstreamer0.8-cdparanoia gstreamer0.8-dv
  gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-flac gstreamer0.8-gnomevfs
.....
376 upgraded, 83 newly installed, 18 to remove and 4 not upgraded.
Remv akode [4:3.4.3-0ubuntu1]
Remv k3b [0.12.7-1ubuntu1~breezy1]
Remv k3blibs [0.12.7-1ubuntu1~breezy1]
Inst liblockdev1 [1.0.1-7] (1.0.2-1 Ubuntu:6.06/dapper)
Inst libqt3-mt [3:3.3.4-8ubuntu5] (3:3.3.6-1ubuntu3 Ubuntu:6.06/dapper)
Inst qobex [0.99+1.0beta1-2ubuntu3] (0.99+1.0beta1-6ubuntu8 Ubuntu:6.06/dapper)
Inst kdebluetooth [0.99+1.0beta1-2ubuntu3] (0.99+1.0beta1-6ubuntu8 Ubuntu:6.06/dapper) []
...
Inst artsbuilder [4:3.4.3-0ubuntu1] (4:3.5.2-0ubuntu3 Ubuntu:6.06/dapper) []
...
Inst arts [1.4.3-0ubuntu1] (1.5.2-0ubuntu1 Ubuntu:6.06/dapper) []
...
Inst audacity [1.2.3-1build2] (1.2.4b-2ubuntu2 Ubuntu:6.06/dapper)
...
Inst bogofilter [0.95.2-1ubuntu1.1] (1.0.1-1ubuntu1 Ubuntu:6.06/dapper)
...
etc etc.

So, I thought, let's see what versions of some of these are actually installed already:
root@centaur:~ # dpkg -s arts
Package: arts
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 36
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: all
Version: 1.4.3-0ubuntu1
Depends: libartsc0 (>= 1.4.3-0ubuntu1), libarts1c2 (>= 1.4.3-0ubuntu1)
Description: Analog Realtime Synthesizer (aRts) metapackage
 aRts is a short form for "analog realtime synthesizer". The idea of the whole
 thing is to create/process sound using small modules which do certain tasks.
 These may be create a waveform (oscillators), play samples, filter data, add
 signals, perform effects like delay/flanger/chorus, or output the data to
 the soundcard.
 .
 aRts is the core sound system for KDE (and other systems).
 .
 This package is part of the official KDE aRts module.
root@centaur:~ # dpkg -s artsbuilder audacity bogofilter
Package: artsbuilder
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 9700
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: kdemultimedia
Version: 4:3.4.3-0ubuntu1
Replaces: kdebase-data (<< 4:3.3.91)
Depends: kdelibs4c2 (>= 4:3.4.3), libart-2.0-2 (>= 2.3.16), libarts1c2 (>= 1.3.2) , libasound2 (>> 1.0.9), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.3.4-1 ), libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35), libfontconfig1 (>= 2.3.0), lib freetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.1), libglib2.0-0 (>= 2.8.0),  libice6, libidn11 (>= 0.5.13), libjpeg62, libogg0 (>= 1.1.2), libpng12-0 (>= 1.2 .8rel), libqt3-mt (>= 3:3.3.4), libsm6, libstdc++6 (>= 4.0.1), libvorbis0a (>= 1. 1.0), libvorbisenc2 (>= 1.1.0), libvorbisfile3 (>= 1.1.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxr ender1, libxt6, zlib1g (>= 1:1.2.1)
Suggests: khelpcenter
Description: synthesizer designer for aRts
 This is the analog Realtime synthesizer's graphical design tool.
 .
 This package is part of KDE, as a component of the KDE multimedia module.
 See the 'kde' and 'kdemultimedia' packages for more information.
Package: audacity
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 4708
Maintainer: Matt Brubeck <mbrubeck@cs.hmc.edu>
Architecture: i386
Version: 1.2.3-1build2
Depends: libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.1), libid3tag0 (>= 0.15.1b), libma d0 (>= 0.15.1b), libogg0 (>= 1.1.2), libsndfile1 (>= 1.0.2-1), libstdc++6 (>= 4.0 .1), libvorbis0a (>= 1.1.0), libvorbisenc2 (>= 1.1.0), libvorbisfile3 (>= 1.1.0),  libwxgtk2.4-1 (>= 2.4.4ubuntu5)
Suggests: ladspa-plugin
Description: A fast, cross-platform audio editor
 Audacity is a multi-track audio editor for Linux/Unix, MacOS and
 Windows.  It is designed for easy recording, playing and editing of
 digital audio.  Audacity features digital effects and spectrum
 analysis tools.  Editing is very fast and provides unlimited
 undo/redo.
 .
 Supported file formats include Ogg Vorbis, MP3, WAV, AIFF, and AU.
 .
 For more information, see [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/).

Package: bogofilter
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 20
Maintainer: Clint Adams <schizo@debian.org>
Architecture: i386
Version: 0.95.2-1ubuntu1.1
Depends: bogofilter-bdb
Description: a fast Bayesian spam filter (dummy package)
 This package implements a fast Bayesian spam filter along the lines suggested
 by Paul Graham in his article "A Plan For Spam".
 .
 This version substantially improves on Paul's proposal by doing smarter
 lexical analysis.  In particular, hostnames and IP addresses are retained
 as recognition features rather than broken up. Various kinds of MTA
 cruft such as dates and message-IDs are discarded so as not to bloat
 the word lists.
root@centaur:~ #

So, as we see, EXACTLY THE SAME VERSIONS are *already* installed OK!

I'd rather not rather not burden the already busy servers at ubuntu by doing what looks like a totally unnecessary re-apt-get-dist-upgrade. That was the point of getting the cdrom image via bittorrent in the first place anyway!

Please can someone come with a magic incantation to give my system a cluebat that IT's ALREADY UPGRADED!

---

