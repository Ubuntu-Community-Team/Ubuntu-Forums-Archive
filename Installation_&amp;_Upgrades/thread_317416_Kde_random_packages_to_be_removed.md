---
title: "Kde random packages to be removed"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by soapytheclown on 2006-12-12
hi all, 
      i used to use ubuntu but from initally using slackware and kde i soon installed the kubuntu-desktop package and everything has been working great apart from the odd hicup here and there mostly to do with beryl however today i was "apt-get"ting something and i got the following message:-

The following packages were automatically installed and are no longer required:
  kpdf ksystemlog krdc krfb kscd kppp libktnef1 konversation
  kubuntu-default-settings python2.4-dev kdeprint adept-manager
  kmplayer-konq-plugins ksvg kscreensaver kaffeine-xine
  libavahi-compat-libdnssd1 kio-locate libk3b2 libpythonize0 ksnapshot
  liblockdev1 kdebluetooth kooka libkipi0 wlassistant mplayer-skins libkcal2b
  openoffice.org-kde libmagick++9c2a adept-installer libkexif1
  kdegraphics-kfile-plugins konqueror-nsplugins gwenview libpoppler1-qt
  libtdb1 libmp4v2-0 adept-updater kdepim-kio-plugins qca-tls libmimelib1c2a
  klipper kubuntu-artwork-usplash kontact kdeadmin-kfile-plugins ksmserver
  ksysguard adept-batch kde-icons-mono kmenuedit pykdeextensions adept
  ksplash-engine-moodin kubuntu-konqueror-shortcuts ksplash kaffeine
  libkleopatra1 skim kipi-plugins korganizer k3b kdenetwork-kfile-plugins
  kbstate akregator kio-apt kwin-style-crystal arts python-qt3 ark libexif-dev
  libgphoto2-2-dev kcron libjasper-runtime adept-common libksieve0 digikam
  amarok-xine libkpimidentities1 amarok libskim0 kpf bogofilter-bdb
  libkdepim1a kdnssd kdemultimedia-kfile-plugins katapult poster
  kdenetwork-filesharing kubuntu-docs knotes bogofilter libtunepimp3
  kde-guidance libifp4 debtags docker libgsl0 khelpcenter apt-index-watcher
  kaddressbook libkpimexchange1 gtk2-engines-gtk-qt kmailcvt rdiff-backup
  knetworkconf ksysguardd konq-plugins libkmime2 psutils language-selector-qt
  qobex ktorrent libgpgme11 scim-qtimm kwalletmanager kopete karm kate kmail
  keep tomcat5.5-admin adept-notifier bogofilter-common libimlib2
  kde-guidance-powermanager kde-systemsettings librsync1 kmousetool kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base kaudiocreator
  python-kde3 kdepasswd kmix
Use 'apt-get autoremove' to remove them.


surely somthing is wrong there some of those look like fairly important kde apps can anyone help me resolve this and get it to not want to remove kde?? 

cheers

---

### Post by pay on 2006-12-14
I think that that happens if you mix aptitude with apt-get and then one of them gets confussed (don't quote me!). You can always reinstall the packages needed for kde with ```
sudo aptitude install kubuntu-desktop
```If you don accidently remove them. Maybe someone with some more knowledge will help you out more than me though.

---

