---
title: "Aptitude's --without-recommends doesn't seem to work"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Nameless_one on 2008-02-20
I want to try out KDE, and want to install the kubuntu-desktop package, although without the recommended packages. I generally use aptitude, and very much want to use it with this, because after I look around I would like to sudo aptitude remove kubuntu-desktop and be done with all the extra KDE packages. 

Aptitude's manual page mentions an option 
```
-R, --without-recommends
           Do not treat recommendations as dependencies when installing new packages (this overrides settings in /etc/apt/apt.conf and ~/.aptitude/config). Packages
           previously installed due to recommendations will not be removed.

```

however it doens't seem to work. Here is why: 
```
Package: kubuntu-desktop
State: not installed
Version: 1.59
Priority: optional
Section: metapackages
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Uncompressed Size: 45.1k
Depends: acpi, acpi-support, acpid, anacron, apmd, ark, arts, avahi-daemon, bc, cupsys, cupsys-bsd, cupsys-client, dbus, dc, foomatic-db, foomatic-db-engine, foomatic-db-hpijs,
         foomatic-filters, genisoimage, ghostscript-x, hal, hotkey-setup, hwdb-client-kde, kcontrol, kcron, kde-guidance, kde-style-polyester, kde-systemsettings,
         kdeadmin-kfile-plugins, kdebase-kio-plugins, kdegraphics-kfile-plugins, kdemultimedia-kfile-plugins, kdemultimedia-kio-plugins, kdenetwork-filesharing,
         kdenetwork-kfile-plugins, kdepasswd, kdeprint, kdesktop, kdm, kdnssd, kghostview, khelpcenter, kicker, kio-apt, kio-locate, kmenuedit, kmix, knetworkconf, konq-plugins,
         konsole, kpdf, ksmserver, ksnapshot, ksplash, ksplash-engine-moodin, ksvg, ksystemlog, kubuntu-artwork-usplash, kwin, language-selector-qt, lftp, libarts1-akode,
         libgl1-mesa-glx, libglut3, libpam-foreground, libqt-perl, libsasl2-modules, libxp6, openprinting-ppds, pnm2ppa, powermanagement-interface, qca-tls, readahead, screen,
         slocate, smbclient, software-properties-kde, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, unzip, usplash, vorbis-tools, x-ttcidfont-conf, xkb-data, xorg, zip
Recommends: adept, akregator, amarok, apport-qt, avahi-autoipd, bluez-cups, bluez-utils, bogofilter, brltty, cdparanoia, cdrdao, cups-pdf, digikam, discover1, dolphin,
            dvd+rw-tools, foo2zjs, foomatic-db-gutenprint, fortune-mod, gcc, gdebi-kde, gtk-qt-engine, gwenview, hplip, hplip-gui, k3b, kaddressbook, kaffeine-xine, kamera, karm,
            katapult, kate, kbstate, kde-guidance-powermanager, kde-icons-mono, kdebluetooth, kdepim-kio-plugins, kdepim-wizards, kdesudo, keep, kfind, kio-umountwrapper,
            kipi-plugins, klipper, kmag, kmail, kmailcvt, kmilo, kmousetool, kmplayer-konq-plugins, knotes, konqueror, konqueror-nsplugins, kontact, konversation, kooka, kopete,
            korganizer, kpf, kppp, krdc, krfb, kscreensaver, ksysguard, ktorrent, kubuntu-default-settings, kubuntu-docs, kubuntu-konqueror-shortcuts, kvkbd, kwalletmanager,
            landscape-client, laptop-detect, libgl1-mesa-dri, libnss-mdns, linux-headers-generic, make, min12xxw, network-manager-kde, networkstatus, openoffice.org-calc,
            openoffice.org-draw, openoffice.org-impress, openoffice.org-java-common, openoffice.org-kde, openoffice.org-math, openoffice.org-writer, pinentry-qt, powernowd, pxljr,
            rdesktop, restricted-manager-kde, scim-qtimm, skim, speedcrunch, splix, strigi-applet, strigi-daemon, ttf-arabeyes, ttf-arphic-ukai, ttf-arphic-uming, ttf-gentium,
            ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-mgopen, ttf-thai-tlwg, ttf-unfonts-core, wodim, wvdial, xcursor-themes,
            xdg-utils, xresprobe
Description: Kubuntu desktop system
 This package depends on all of the packages in the Kubuntu desktop system 
 
 It is safe to remove this package if some of the desktop system packages are not desired.

nameless@shadowfortress:~$ sudo aptitude install -R kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater amarok-xine debtags enscript fftw3 gnupg-agent gpgsm ijsgutenprint kaffeine 
  kdebase-bin kdebase-data kdelibs-data kdelibs4c2a kdepim-kresources kdesktop kfind kicker kmplayer-base konqueror konsole korganizer ksysguardd kwin kwin-style-crystal 
  libakode2 libarts1c2a libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgpgme11 libifp4 libijs-0.35 libimlib2 libjpeg-progs 
  libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 
  libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpth20 libpythonize0 
  libqt4-core libqt4-gui librsync1 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 
  libxcb-xv0 libxcb1 libxine1 mysql-common networkstatus openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 
  python-qt4-dbus python-sip4 python2.5-dev rdiff-backup 
The following NEW packages will be installed:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript 
  fftw3 foo2zjs foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine 
  kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins 
  kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins 
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview 
  khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins 
  knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot 
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs 
  kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libavahi-qt3-1 libclucene0 
  libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgpgme11 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 
  libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 
  libmimelib1c2a libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpth20 libpythonize0 libqt-perl libqt4-core libqt4-gui librsync1 
  libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 
  mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 
  python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde scim-qtimm skim software-properties-kde speedcrunch strigi-applet 
  strigi-daemon ttf-arphic-ukai 
0 packages upgraded, 206 newly installed, 0 to remove and 0 not upgraded.
Need to get 206MB of archives. After unpacking 699MB will be used.
Do you want to continue? [Y/n/?] 

```

As you can see, all recommended packages of kubuntu-desktop are included in the list of packages that will be installed. 

I probably can do this using Synaptic or apt-get, but I don't know how, I am not sure if I will be able to reverse it, and I also want to learn how to do it with aptitude because it's my preffered application and want to keep it updated about package status in my system. 

Any ideas?

---

### Post by PmDematagoda on 2008-02-20
Perhaps you could install the kde-core package instead of the kubuntu-desktop package, the kde-core package contains only the bare essentials to use KDE.

---

### Post by Nameless_one on 2008-02-20
Yes, that looks right. However, the problem with aptitude remains and I'd like to find a way to install without recommends, for general use. Thank you for the reply.

---

### Post by Nameless_one on 2008-02-21
Bump?

---

