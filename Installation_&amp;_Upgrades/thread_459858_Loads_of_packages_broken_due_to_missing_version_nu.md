---
title: "Loads of packages broken due to missing version number"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by guttingfish on 2007-05-31
I started to update this morning and got a load of broken packages, so I checked it out in a terminal and got the errors below. I updated only a day or two ago, and it was fine then. I tried rebooting just in case, but had no joy.

I've tested a few of the programs below and they all seem to work. Anyone have any ideas what the hell is going on?

```

[09:30:28][jd@isis]$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  kpdf: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kwin-style-blended: Depends: libqt3-mt (>= 3:3.3.5) but  is installed.
  ksystemlog: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  libavahi-qt3-1: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  krdc: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  ksplash-engine-moodin: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  krec: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  libpopt0: Conflicts: rpm (<= ) but 4.4.1-14build1 is installed.
  krfb: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libarts1c2a: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kscd: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  kppp: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kdelibs4c2a: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  ksig: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kipi-plugins: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  artsbuilder: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  ktip: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kdeprint: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  ksvg: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kruler: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kpersonalizer: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libgnome2-0: Depends: libpopt0 (>= 1.10) but  is installed.
  kdiff3: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  gtk-qt-engine: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kdepim-kio-plugins: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kwin: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
        Depends: libxcomposite1 (>= 1:0.3-1) but (null) is installed.
  kio-locate: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  atlantikdesigner: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libk3b2: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  smbclient: Depends: libpopt0 (>= 1.10) but  is installed.
  whiptail: Depends: libpopt0 (>= 1.10) but  is installed.
  ksnapshot: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kpackage: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kooka: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kcontrol: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libkipi0: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kcontrol-autostart: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  adept-installer: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libkcal2b: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  evolution: Depends: libpopt0 (>= 1.10) but  is installed.
  konqueror-nsplugins: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libgnomeui-0: Depends: libpopt0 (>= 1.10) but  is installed.
  libecal1.2-7: Depends: libpopt0 (>= 1.10) but  is installed.
  kpager: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  gwenview: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  python-gnome2-extras: Depends: libpopt0 (>= 1.10) but  is installed.
  : Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kdeaddons-kfile-plugins: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kde-guidance: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  logrotate: Depends: libpopt0 (>= 1.7) but  is installed.
  qca-tls: Depends: libqt3-mt (>= 3:3.3.5) but  is installed.
  klipper: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  librpm4: Depends: libpopt0 (>= 1.10) but  is installed.
  kmplayer-base: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kaudiocreator: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  libedata-cal1.2-6: Depends: libpopt0 (>= 1.10) but  is installed.
  kaddressbook: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kontact: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kicker: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
          Depends: libxcomposite1 (>= 1:0.3-1) but (null) is installed.
  kwalletmanager: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kwin-style-alphacube: Depends: libqt3-mt (>= 3:3.3.5) but  is installed.
  ksmserver: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  ksysguard: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  adept-batch: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  liblpint-bonobo0: Depends: libpopt0 (>= 1.10) but  is installed.
  konq-plugins: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kdepim-kresources: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kmenuedit: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  gtkhtml3.14: Depends: libpopt0 (>= 1.10) but  is installed.
  ksplash: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kaffeine: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kaffeine-xine: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  skim: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  korganizer: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  openoffice.org-kde: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  k3b: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  samba-common: Depends: libpopt0 (>= 1.10) but  is installed.
  atlantik: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  akregator: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kio-apt: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libgnomeprint2.2-0: Depends: libpopt0 (>= 1.10) but  is installed.
  python-qt3: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libgnome-desktop-2: Depends: libpopt0 (>= 1.10) but  is installed.
  ark: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kcron: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  superkaramba: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  noatun-plugins: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kde-systemsettings: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  koffice-libs: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kdegraphics-kfile-plugins: Depends: libpoppler1-qt (>= 0.5.1) but  is installed.
                             Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libedataserverui1.2-8: Depends: libpopt0 (>= 1.10) but  is installed.
  kdmtheme: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  ksysv: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libpanel-applet2-0: Depends: libpopt0 (>= 1.10) but  is installed.
  knetworkmanager: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libedata-book1.2-2: Depends: libpopt0 (>= 1.10) but  is installed.
  kmplayer-konq-plugins: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libksieve0: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kuser: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kfind: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libgtkhtml3.14-19: Depends: libpopt0 (>= 1.10) but  is installed.
  kdebase-bin: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kwin-style-suse2: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kdm: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  amarok: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libskim0: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  juk: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  libkdepim1a: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  noatun: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  libexchange-storage1.2-3: Depends: libpopt0 (>= 1.10) but  is installed.
  rsync: Depends: libpopt0 (>= 1.10) but  is installed.
  kghostview: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  katapult: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  knotes: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  samba: Depends: libpopt0 (>= 1.10) but  is installed.
  libdbus-qt-1-1c2: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  khelpcenter: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kicker-kblogger: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  kdesktop: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  rpm: Depends: libpopt0 (>= 1.10) but  is installed.
  konqueror: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kaboodle: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  kmailcvt: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kscreensaver: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  vim-full: Depends: libpopt0 (>= 1.10) but  is installed.
  kdebase-kio-plugins: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libkleopatra1: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  qobex: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libbonoboui2-0: Depends: libpopt0 (>= 1.10) but  is installed.
  adept-manager: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  ktorrent: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  totem-xine: Depends: libpopt0 (>= 1.10) but  is installed.
  scim-qtimm: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  evolution-data-server: Depends: libpopt0 (>= 1.10) but  is installed.
  kdepim-wizards: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libkpimidentities1: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kappfinder: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kwin-style-crystal: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kdat: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  karm: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kate: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kmail: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kscreensaver-xsavers: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  keep: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  secpolicy: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  adept-notifier: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  libk3b2-mp3: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kwin-style-powder: Depends: libqt3-mt (>= 3:3.3.5) but  is installed.
  kexi: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  librsync1: Depends: libpopt0 (>= 1.7) but  is installed.
  kmousetool: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  adept-updater: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kmag: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  libgdl-1-0: Depends: libpopt0 (>= 1.10) but  is installed.
  kmilo: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kompose: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  python-gnome2-desktop: Depends: libpopt0 (>= 1.10) but  is installed.
  python-kde3: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  kmid: Depends: libqt3-mt (>= 3:3.3.8) but  is installed.
  yakuake: Depends: libqt3-mt (>= 3:3.3.7) but  is installed.
  networkstatus: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kdepasswd: Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but  is installed.
  kooldock: Depends: libqt3-mt (>= 3:3.3.6) but  is installed.
  libebook1.2-9: Depends: libpopt0 (>= 1.10) but  is installed.

```

---

