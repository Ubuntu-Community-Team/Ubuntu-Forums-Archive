---
title: "Aptitude wants to remove many packages post upgrade"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by casperl on 2010-05-13
Using Xubuntu, I have upgraded from Karmic to Lucid.  Post upgrading when attempting to install a new package with aptitude, it is reported that cups is "BROKEN" and a host of packages are marked for removal.  This is NOT what I want to do at all...

How do I fix this horrible mess?

> 
sudo aptitude install xpdf-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  cups 
The following NEW packages will be installed:
  xpdf-common{a} xpdf-utils 
The following packages will be REMOVED:
  adblock-plus{u} autoconf2.13{u} automake1.4{u} dmraid{u} feh{u} 
  firefox-3.5-gnome-support{u} gnome-blackjack{u} 
  kdebase-runtime-bin-kde4{u} kdebase-runtime-data-common{u} 
  kdebase-workspace-libs4+5{u} kpartx{u} libass3{u} libbind9-50{u} 
  libboost-date-time1.38.0{u} libboost-program-options1.38.0{u} 
  libboost-regex1.38.0{u} libboost-thread1.38.0{u} libc-client2007b{u} 
  libcdio7{u} libcelt0{u} libcln5{u} libcompress-bzip2-perl{u} 
  libcups2-dev{u} libcv1{u} libcv4{u} libcvaux1{u} libcvaux4{u} 
  libdmraid1.0.0.rc15{u} libdmraid1.0.0.rc16{u} libdns50{u} libexiv2-5{u} 
  libfaac0{u} libfaad0{u} libffado1{u} libfreebob0{u} libgcrypt11-dev{u} 
  libgda-4.0-4{u} libgda-4.0-common{u} libgdata5{u} libgdl-1-3{u} 
  libgnutls-dev{u} libgoffice-0-4{u} libgoffice-0-8-common{u} 
  libgoffice-0-common{u} libgpg-error-dev{u} libgsf-gnome-1-114{u} 
  libgssdp-1.0-1{u} libgupnp-1.0-2{u} libhighgui1{u} libhighgui4{u} 
  libhsqldb-java{u} libicu40{u} libindicate-gtk1{u} libindicate3{u} 
  libisc50{u} libisccc50{u} libisccfg50{u} libiso9660-5{u} 
  libknotificationitem1{u} liblo0ldbl{u} liblsofui4{u} liblwres50{u} 
  liblzma0{u} libmaa1{u} libmysqlclient15off{u} libntfs-3g54{u} 
  libpolkit-dbus2{u} libpolkit-gnome0{u} libpolkit-grant2{u} 
  libpolkit-qt0{u} libpolkit2{u} libqt4-phonon{u} librasqal1{u} 
  libservlet2.4-java{u} libservlet2.5-java{u} libstrigiqtdbusclient0{u} 
  libtalloc1{u} libtasn1-3-dev{u} libx264-67{u} libxklavier15{u} 
  mplayer-skins{u} openoffice.org{u} openoffice.org-base{u} 
  openoffice.org-filter-binfilter{u} openoffice.org-filter-mobiledev{u} 
  openoffice.org-hyphenation{u} openoffice.org-hyphenation-af{u} 
  openoffice.org-hyphenation-en-us{u} openoffice.org-java-common{u} 
  openoffice.org-officebean{u} openoffice.org-report-builder-bin{u} 
  openoffice.org-thesaurus-en-au{u} openoffice.org-thesaurus-en-us{u} 
  policykit{u} policykit-gnome{u} poppler-utils{a} python-docutils{u} 
  python-eggtrayicon{u} python-gda{u} python-gdl{u} python-gksu2{u} 
  python-gtksourceview{u} python-nautilusburn{u} python-openssl{u} 
  python-pam{u} python-pyasn1{u} python-pygments{u} python-roman{u} 
  python-serial{u} python-sip4{u} python-transaction{u} python-twisted{u} 
  python-twisted-bin{u} python-twisted-conch{u} python-twisted-core{u} 
  python-twisted-lore{u} python-twisted-mail{u} python-twisted-names{u} 
  python-twisted-news{u} python-twisted-runner{u} python-twisted-web{u} 
  python-twisted-words{u} python-zc.lockfile{u} python-zconfig{u} 
  python-zdaemon{u} python-zodb{u} python-zope.proxy{u} python2.4{u} 
  python2.5{u} qcad-data{u} qcad-doc{u} qt3-assistant{u} qt3-doc{u} 
  raptor-utils{u} redland-utils{u} sdparm{u} seamonkey-gnome-support{u} 
  sivp{u} texlive-base-bin-doc{u} texlive-generic-extra{u} 
  texlive-humanities{u} texlive-humanities-doc{u} ttf-sil-gentium{u} 
  ttf-sil-gentium-basic{u} xsplash{u} xul-ext-adblock-plus{u} 
  xulrunner-1.9.1{u} xulrunner-1.9.1-gnome-support{u} 
0 packages upgraded, 2 newly installed, 148 to remove and 0 not upgraded.
Need to get 2,109kB of archives. After unpacking 315MB will be freed.
The following packages have unmet dependencies:
  cups: Depends: poppler-utils (>= 0.12) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
bluez-cups
cups
cups-driver-gutenprint
cupsys-driver-gutenprint
foo2zjs
foomatic-db
foomatic-db-engine
foomatic-db-gutenprint
ghostscript-cups
hpijs-ppds
hplip
kbluetooth
kubuntu-desktop
openprinting-ppds
pxljr
splix
xubuntu-desktop

Keep the following packages at their current version:
python2.4 [2.4.6-1ubuntu3 (now)]
python2.5 [2.5.4-1ubuntu6 (now)]

Leave the following dependencies unresolved:
foomatic-filters recommends foomatic-db-engine
foomatic-filters recommends poppler-utils (>= 0.11.2)
hpijs recommends cups
min12xxw recommends cups
min12xxw recommends foomatic-db
min12xxw recommends foomatic-db-engine
ijsgutenprint recommends foomatic-db-gutenprint
bluetooth recommends bluez-cups
Score is -595

Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

Remove the following packages:
bluez-cups
cups
cups-driver-gutenprint
cupsys-driver-gutenprint
foo2zjs
foomatic-db
foomatic-db-engine
foomatic-db-gutenprint
ghostscript-cups
hpijs-ppds
hplip
kbluetooth
kubuntu-desktop
openprinting-ppds
pxljr
splix
xubuntu-desktop

Keep the following packages at their current version:
python2.5 [2.5.4-1ubuntu6 (now)]

Leave the following dependencies unresolved:
foomatic-filters recommends foomatic-db-engine
foomatic-filters recommends poppler-utils (>= 0.11.2)
hpijs recommends cups
min12xxw recommends cups
min12xxw recommends foomatic-db
min12xxw recommends foomatic-db-engine
ijsgutenprint recommends foomatic-db-gutenprint
bluetooth recommends bluez-cups
python2.4-minimal recommends python2.4
Score is -866

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.



---

### Post by mörgæs on 2010-05-13
This mess happens sometimes with upgrades. The best I can suggest is a clean install.

---

