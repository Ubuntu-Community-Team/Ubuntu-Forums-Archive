---
title: "Adding Kde Desktop"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by frrobert on 2006-12-01
I tried to install the kde desktop on Ubuntu 6.06  and get the following

frrobert@frrobert-laptop:~$ sudo aptitude install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-ppp
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode libgpgme11
  libifp4 libiso9660-4 libjasper-runtime libjpeg-progs libk3b2 libkcal2b
  libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1
  libmimelib1c2a libpoppler1-qt libpythonize0 libqt-perl librsync1
  libruby1.8 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp3
  libvcdinfo0 libvisual-0.4-0 libvisual-0.4-plugins ncompress ocrad
  openoffice.org-kde poster postfix procmail psutils pykdeextensions
  python-kde3 python-qt3 python2.4-dev python2.4-kde3 python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex rdiff-backup resolvconf ruby ruby1.8
  scim-qtimm skim speedcrunch ssl-cert vcdimager wlassistant zoo
The following packages have been kept back:
  kino
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libgpgme11 libifp4 libiso9660-4 libjasper-runtime
  libjpeg-progs libk3b2 libkcal2b libkdepim1a libkexif1 libkipi0
  libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 liblockdev1 libmimelib1c2a libpoppler1-qt
  libpythonize0 libqt-perl librsync1 libruby1.8 libsensors3 libskim0
  libsmokeqt1 libtdb1 libtunepimp3 libvcdinfo0 libvisual-0.4-0
  libvisual-0.4-plugins ncompress ocrad openoffice.org-kde poster postfix
  procmail psutils pykdeextensions python-kde3 python-qt3 python2.4-dev
  python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex
  rdiff-backup resolvconf ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert
  vcdimager wlassistant zoo
0 packages upgraded, 155 newly installed, 0 to remove and 1 not upgraded.
Need to get 112MB/134MB of archives. After unpacking 393MB will be used.
The following packages have unmet dependencies:
  gnome-ppp: Conflicts: resolvconf but 1.34ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
fetchmail [6.3.2-2ubuntu2 (dapper, dapper)]

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
postfix [Not Installed]
resolvconf [Not Installed]

Score is -7

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
frrobert@frrobert-laptop:~$ sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-ppp
The following NEW packages will be automatically installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal
  language-selector-qt latex-xft-fonts libakode2 libarts1-akode libgpgme11
  libifp4 libiso9660-4 libjasper-runtime libjpeg-progs libk3b2 libkcal2b
  libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkpimexchange1
  libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1
  libmimelib1c2a libpoppler1-qt libpythonize0 libqt-perl librsync1
  libruby1.8 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp3
  libvcdinfo0 libvisual-0.4-0 libvisual-0.4-plugins ncompress ocrad
  openoffice.org-kde poster postfix procmail psutils pykdeextensions
  python-kde3 python-qt3 python2.4-dev python2.4-kde3 python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex rdiff-backup resolvconf ruby ruby1.8
  scim-qtimm skim speedcrunch ssl-cert vcdimager wlassistant zoo
The following packages have been kept back:
  kino
The following NEW packages will be installed:
  adept akregator amarok amarok-xine ark arts artsbuilder dcraw debtags
  flac gtk2-engines-gtk-qt gwenview k3b kaddressbook kaffeine kaffeine-xine
  karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdm kdnssd
  keep khelpcenter kio-apt kio-locate kipi-plugins kitchensync
  klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base
  kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs
  konq-plugins konqueror-nsplugins kontact konversation kooka kopete
  korganizer kpdf kpersonalizer kpf kppp krdc kregexpeditor krfb krita
  krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot
  ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop
  kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager
  kwin-style-crystal language-selector-qt latex-xft-fonts libakode2
  libarts1-akode libgpgme11 libifp4 libiso9660-4 libjasper-runtime
  libjpeg-progs libk3b2 libkcal2b libkdepim1a libkexif1 libkipi0
  libkleopatra1 libkmime2 libkpimexchange1 libkpimidentities1 libkscan1
  libksieve0 libktnef1 liblockdev1 libmimelib1c2a libpoppler1-qt
  libpythonize0 libqt-perl librsync1 libruby1.8 libsensors3 libskim0
  libsmokeqt1 libtdb1 libtunepimp3 libvcdinfo0 libvisual-0.4-0
  libvisual-0.4-plugins ncompress ocrad openoffice.org-kde poster postfix
  procmail psutils pykdeextensions python-kde3 python-qt3 python2.4-dev
  python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex
  rdiff-backup resolvconf ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert
  vcdimager wlassistant zoo
0 packages upgraded, 155 newly installed, 0 to remove and 1 not upgraded.
Need to get 112MB/134MB of archives. After unpacking 393MB will be used.
The following packages have unmet dependencies:
  gnome-ppp: Conflicts: resolvconf but 1.34ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
fetchmail [6.3.2-2ubuntu2 (dapper, dapper)]

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
postfix [Not Installed]
resolvconf [Not Installed]

Score is -7

Accept this solution? [Y/n/q/?]


Any ideas?

Thanks,

Fr. Robert

---

### Post by lemonsCC on 2006-12-01
you may want to accept by typing "y"

did you run ```
sudo apt-get update && sudo apt-get upgrade
``` prior to trying to install?

---

### Post by thelocust on 2006-12-01
[SIZE="2"]**Good call on KDE it's uber better than Gnome. I would suggest saving your home file and source.list file and install kubuntu. Trust me once you see KDE you will never look back.**[/SIZE] :cool:

---

### Post by frrobert on 2006-12-01
Got it installed.  Had to remove Gnome PPP to get it to work.

---

### Post by lemonsCC on 2006-12-02
> **thelocust said:**
> [SIZE="2"]**Good call on KDE it's uber better than Gnome. I would suggest saving your home file and source.list file and install kubuntu. Trust me once you see KDE you will never look back.**[/SIZE] :cool:

NEVER!!!!:mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

