---
title: "Accidently tried to remove libsdl1.2-dev libsdl1.2debian"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by sixsidepentagon on 2007-10-14
I accidentally issued the command sudo apt-get remove libsdl1.2-dev libsdl1.2debian, and it promptly began to delete something that I think was called "kubuntu -desktop" and "armegetron common". It was going to remove more, but I ctrl + c'd, but it might have gotten a couple other things. Now I'm panicking: is it even safe to turn off the computer? Will I be able to get back into kubuntu? When I try to sudo aptitude upgrade, it gives me this lift of to be removed things:
The following packages are unused and will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark
  arts debtags digikam digikamimageplugins exiv2 fftw3 gtk-qt-engine
  gwenview hwdb-client-kde imagemagick k3b kaffeine kaffeine-xine karm
  katapult kate kbstate kcron kde-guidance kde-guidance-powermanager
  kde-icons-mono kde-style-polyester kde-systemsettings
  kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins
  kdemultimedia-kfile-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kresources kdepim-wizards
  kdeprint kdm kdnssd keep kexi khelpcenter kio-apt kio-locate kipi-plugins
  kitchensync klipper kmag kmailcvt kmenuedit kmilo kmix kmousetool
  knetworkconf knode knotes koffice-data koffice-libs konq-plugins
  konqueror-nsplugins kontact konversation kooka kopete korganizer kpdf
  kpersonalizer kpf kppp krdc kregexpeditor krfb kscreensaver
  kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin
  ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts
  kwin-style-crystal language-selector-qt latex-xft-fonts
  libavahi-compat-libdnssd1 libcurl3-gnutls libexiv2-0.12 libflac++5c2
  libgmp3c2 libifp4 libimlib2 libiso9660-4 libjasper-runtime libjpeg-progs
  libk3b2 libkexiv2-0 libkipi0 libkpimexchange1 libkscan1 liblockdev1
  libmeanwhile1 libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off
  libnjb5 libofa0 libopenobex1 libpoppler1-qt libpq5 libpulse0
  libpythonize0 libqt-perl libqt4-core libqt4-gui libqt4-qt3support
  libqt4-sql librsync1 libruby1.8 libskim0 libsmokeqt1 libsqlite0 libtdb1
  libtunepimp5 libvcdinfo0 libxine1 libxine1-ffmpeg libxvmc1 mysql-common
  ncompress ocrad p7zip-full poster psutils pykdeextensions python-all
  python-all-dev python-elementtree python-kde3 python-qt4 python2.4
  python2.4-dev python2.4-minimal qca-tls qobex qt4-qtconfig rdiff-backup
  ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch
  vcdimager vorbis-tools zoo

What now? And I'm sorry if this is the wrong place to post, but I'm a bit panicked right now.

---

### Post by smartbei on 2007-10-14
Just do:
```

sudo aptitude install kubuntu-desktop

```
That is the metapackage that depends on that long list of packages aptitude wanted to install.

---

