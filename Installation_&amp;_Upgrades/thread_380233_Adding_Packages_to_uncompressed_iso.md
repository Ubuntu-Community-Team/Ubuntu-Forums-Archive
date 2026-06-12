---
title: "Adding Packages to uncompressed iso"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by kevanr on 2007-03-09
I have an uncompressd iso image that I am remastering for my own distro, (its a Ubuntu 6.06 iso), I know how to purge packages from it via a terminal. How do I add packages to the iso so that when I re-compress the iso, the programs will work?

---

### Post by linear on 2007-03-09
Should just be **apt-get install**, as detailed [here]("https://help.ubuntu.com/community/LiveCDCustomization"), under "installing Additional Packages" (the page says Hoary/Breezy, but this section applies equally well to Dapper).

---

### Post by kevanr on 2007-03-09
does this install the packages onto my current OS, or the OS i am building?

---

### Post by kevanr on 2007-03-09
I am installing a few programs, so I tried this:

kevan@kevanr:~$ cd ~/live

To have it refer to that directory (I hope) then I started to install files:

kevan@kevanr:~/live$ sudo apt-get install knocker
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls libapr0 klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  knocker
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 27.3kB of archives.
After unpacking 119kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe knocker 0.7.1-3 [27.3kB]
Fetched 27.3kB in 1s (22.3kB/s) 
Selecting previously deselected package knocker.
(Reading database ... 149412 files and directories currently installed.)
Unpacking knocker (from .../knocker_0.7.1-3_i386.deb) ...
Setting up knocker (0.7.1-3) ...
kevan@kevanr:~/live$ sudo apt-get install ipkungfu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls libapr0 klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ipkungfu
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 34.5kB of archives.
After unpacking 217kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe ipkungfu 0.5.2-7 [34.5kB]
Fetched 34.5kB in 1s (27.2kB/s)  
Selecting previously deselected package ipkungfu.
(Reading database ... 149423 files and directories currently installed.)
Unpacking ipkungfu (from .../ipkungfu_0.5.2-7_all.deb) ...
Setting up ipkungfu (0.5.2-7) ...
Not Starting/Stopping ipkungfu: Please read /usr/share/doc/ipkungfu/README.Debian for details
kevan@kevanr:~/live$ sudo apt-get libapache2-mod-security
Password:
E: Invalid operation libapache2-mod-security
kevan@kevanr:~/live$ sudo apt-get install libapache2-mod-security
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-common apache2-utils mod-security-common
Suggested packages:
  apache2-doc
The following NEW packages will be installed:
  apache2-common apache2-utils libapache2-mod-security mod-security-common
0 upgraded, 4 newly installed, 0 to remove and 12 not upgraded.
Need to get 273kB/1173kB of archives.
After unpacking 4248kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main mod-security-common 1.8.7-1ubuntu1 [240kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libapache2-mod-security 1.8.7-1ubuntu1 [33.6kB]
Fetched 273kB in 32s (8356B/s)                                                                  
Selecting previously deselected package apache2-utils.
(Reading database ... 149447 files and directories currently installed.)
Unpacking apache2-utils (from .../apache2-utils_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package mod-security-common.
Unpacking mod-security-common (from .../mod-security-common_1.8.7-1ubuntu1_all.deb) ...
Selecting previously deselected package libapache2-mod-security.
Unpacking libapache2-mod-security (from .../libapache2-mod-security_1.8.7-1ubuntu1_i386.deb) ...
Setting up apache2-utils (2.0.55-4ubuntu4) ...
Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up libapache2-mod-security (1.8.7-1ubuntu1) ...
Setting up mod-security-common (1.8.7-1ubuntu1) ...

kevan@kevanr:~/live$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 719kB of archives.
After unpacking 2494kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main nmap 4.10-1 [719kB]
Fetched 719kB in 11s (63.0kB/s)                                                                 
Selecting previously deselected package nmap.
(Reading database ... 149990 files and directories currently installed.)
Unpacking nmap (from .../archives/nmap_4.10-1_i386.deb) ...
Setting up nmap (4.10-1) ...

kevan@kevanr:~/live$ sudo apt-get install logcheck
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liblockfile1 lockfile-progs logtail mailx
Suggested packages:
  syslog-summary
Recommended packages:
  logcheck-database
The following NEW packages will be installed:
  liblockfile1 lockfile-progs logcheck logtail mailx
0 upgraded, 5 newly installed, 0 to remove and 12 not upgraded.
Need to get 96.6kB/265kB of archives.
After unpacking 844kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main lockfile-progs 0.1.10 [7470B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main logtail 1.2.46 [34.9kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main logcheck 1.2.46 [54.1kB]
Fetched 96.6kB in 6s (16.1kB/s)                                                                 
Preconfiguring packages ...
Selecting previously deselected package liblockfile1.
(Reading database ... 150008 files and directories currently installed.)
Unpacking liblockfile1 (from .../liblockfile1_1.06.1ubuntu1_i386.deb) ...
Selecting previously deselected package lockfile-progs.
Unpacking lockfile-progs (from .../lockfile-progs_0.1.10_i386.deb) ...
Selecting previously deselected package mailx.
Unpacking mailx (from .../mailx_8.1.2-0.20050715cvs-1ubuntu1_i386.deb) ...
Selecting previously deselected package logtail.
Unpacking logtail (from .../logtail_1.2.46_all.deb) ...
Selecting previously deselected package logcheck.
Unpacking logcheck (from .../logcheck_1.2.46_all.deb) ...
Setting up liblockfile1 (1.06.1ubuntu1) ...
Setting up lockfile-progs (0.1.10) ...
Setting up mailx (8.1.2-0.20050715cvs-1ubuntu1) ...

Setting up logtail (1.2.46) ...
Setting up logcheck (1.2.46) ...

kevan@kevanr:~/live$ sudo apt-get install pscan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation krita-data
  kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor kdeprint adept-manager knode
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine libavahi-compat-libdnssd1 kio-locate
  libpythonize0 vorbis-tools ncompress ksnapshot liblockdev1 kdebluetooth kooka libkipi0
  wlassistant openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libsmokeqt1 libpoppler1-qt libtdb1
  adept-updater libqt4-qt3support latex-xft-fonts hwdb-client-kde krita qca-tls klipper
  kubuntu-artwork-usplash libqt4-core kontact libsqlite0 mysql-common kdeadmin-kfile-plugins
  ksmserver ksysguard adept-batch koffice-data kde-icons-mono libcurl3-gnutls libqt-perl
  kmenuedit pykdeextensions adept ksplash-engine-moodin kubuntu-konqueror-shortcuts
  libmysqlclient15off libsvn0 ksplash kaffeine kdesvn-kio-plugins skim kipi-plugins korganizer
  kdenetwork-kfile-plugins kbstate akregator kio-apt kwin-style-crystal arts python-qt3
  python-qt4 ark libexif-dev libgphoto2-2-dev kcron libjasper-runtime adept-common libgmp3c2
  libqt4-gui python-sip4 digikam amarok-xine kdm speedcrunch amarok libskim0 kpf bogofilter-bdb
  kdnssd kdemultimedia-kfile-plugins katapult poster kdenetwork-filesharing kubuntu-docs knotes
  bogofilter ocrad kde-guidance libqt4-sql libifp4 flac debtags libgsl0 khelpcenter
  apt-index-watcher libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup knetworkconf
  ksysguardd konq-plugins libsvnqt2 psutils digikamimageplugins kpersonalizer
  language-selector-qt zoo qobex ktorrent libpq4 scim-qtimm kopete python-elementtree karm kate
  keep koffice-libs adept-notifier bogofilter-common libimlib2 kde-guidance-powermanager
  libjpeg-progs kde-systemsettings librsync1 kmousetool kitchensync libnjb5 kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator python-kde3 qt4-qtconfig
  kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  pscan
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 15.2kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe pscan 1.2-6 [15.2kB]
Fetched 15.2kB in 0s (16.4kB/s)
Selecting previously deselected package pscan.
(Reading database ... 150084 files and directories currently installed.)
Unpacking pscan (from .../archives/pscan_1.2-6_i386.deb) ...
Setting up pscan (1.2-6) ...
kevan@kevanr:~/live$ 

---------------------------------------------------------------------------------------------------------------------
Does this mean that they are installed and will be there when I compress the files and make them into an iso?

---

### Post by kevanr on 2007-03-09
Hello? I really need some verification here...

---

### Post by linear on 2007-03-11
> **kevanr said:**
> does this install the packages onto my current OS, or the OS i am building?

(In my limited experience) as long as you have chroot-ed to the uncompressed LiveCD, as detailed in the wiki, that's where the installation goes.

---

