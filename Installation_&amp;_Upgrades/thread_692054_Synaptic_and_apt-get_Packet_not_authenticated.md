---
title: "Synaptic and apt-get: Packet not authenticated"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by S4nt4 on 2008-02-09
Hello all,

I just did a fresh install of Gutsy. So i have a 250Mb update to do now.

But apt-get and synaptic are telling me that lot of packets can not be authenticated:

```
Souhaitez-vous continuer [O/n] ? ATTENTION : les paquets suivants n'ont pas été authentifiés.
  libc6 libc6-i686 findutils libdb4.4 language-pack-en language-pack-fr
  language-pack-gnome-en language-pack-gnome-fr tzdata libisc32 libdns32
  libisccc30 libisccfg30 libbind9-30 liblwres30 bind9-host dnsutils
  app-install-data-commercial apturl avahi-autoipd libavahi-common-data
  libavahi-common3 libavahi-core5 avahi-daemon bittorrent python-bittorrent
  capplets-data libpango1.0-common libpango1.0-0 libgnomeui-common
  libgnomeui-0 libgnome-desktop-2 libedataserver1.2-9 libcamel1.2-10
  libebook1.2-9 libgnome-menu2 libpanel-applet2-0 gnome-menus python-gmenu
  gnome-desktop-data gnome-control-center libgnome-window-settings1
  libwnck-common libwnck22 libavahi-client3 libavahi-compat-libdnssd1
  libcupsys2 libcupsimage2 libgs8 ghostscript cupsys-common cupsys cupsys-bsd
  cupsys-client deskbar-applet eog ghostscript-x evince libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13
  evolution-data-server evolution-data-server-common libedataserverui1.2-8
  libexchange-storage1.2-3 libgtkhtml3.14-19 libnm-glib0 evolution
  evolution-common gtkhtml3.14 evolution-plugins file-roller foo2zjs gcalctool
  gdm gnome-session libgtksourceview2.0-common libgtksourceview2.0-0
  gedit-common gedit libgimp2.0 gimp-python gimp gimp-data gnome-about
  gnome-games gnome-games-data gnome-cards-data gnome-panel-data gnome-panel
  gnome-system-monitor gtk2-engines hwdb-client-common hwdb-client-gnome
  libavahi-glib1 libnm-util0 linux-restricted-modules-common
  linux-restricted-modules-2.6.22-14-generic network-manager
  openoffice.org-calc python-uno openoffice.org-writer openoffice.org-impress
  openoffice.org-draw openoffice.org-style-human openoffice.org-common
  openoffice.org-java-common openoffice.org-base openoffice.org-gtk
  openoffice.org-gnome openoffice.org-evolution openoffice.org-math
  ttf-opensymbol openoffice.org openoffice.org-core sound-juicer ubufox
  gnome-system-tools
Faut-il installer ces paquets sans vérification (o/N) ?
```

Are they some keys to update ??

---

### Post by PmDematagoda on 2008-02-09
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by S4nt4 on 2008-02-09
Here it is:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by PmDematagoda on 2008-02-09
Your sources.list looks good, post the output of:-
```
sudo apt-get update
```

---

### Post by S4nt4 on 2008-02-09
It's in french, but I'm sure you will recognize most of it.

```
Lecture des listes de paquets...
Construction de l'arbre des dépendances...
Lecture des informations d'état...
Les paquets suivants seront mis à jour :
  app-install-data-commercial apturl avahi-autoipd avahi-daemon bind9-host
  bittorrent capplets-data compiz compiz-core compiz-gnome compiz-plugins
  cupsys cupsys-bsd cupsys-client cupsys-common deskbar-applet dnsutils
  e2fslibs e2fsprogs eog evince evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-plugins
  file-roller findutils firefox firefox-gnome-support foo2zjs gcalctool gdm
  gedit gedit-common ghostscript ghostscript-x gimp gimp-data gimp-python
  gnome-about gnome-cards-data gnome-control-center gnome-desktop-data
  gnome-games gnome-games-data gnome-menus gnome-panel gnome-panel-data
  gnome-screensaver gnome-session gnome-system-monitor gnome-system-tools
  gtk2-engines gtkhtml3.14 hwdb-client-common hwdb-client-gnome
  language-pack-en language-pack-fr language-pack-gnome-en
  language-pack-gnome-fr libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libbind9-30 libblkid1 libc6 libc6-i686 libcairo2 libcamel1.2-10 libcomerr2
  libcupsimage2 libcupsys2 libdb4.4 libdecoration0 libdns32 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libflac8
  libgimp2.0 libgnome-desktop-2 libgnome-menu2 libgnome-window-settings1
  libgnomeui-0 libgnomeui-common libgs8 libgtkhtml3.14-19
  libgtksourceview2.0-0 libgtksourceview2.0-common libisc32 libisccc30
  libisccfg30 libkpathsea4 liblwres30 libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libnm-glib0 libnm-util0
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpcre3 libpcrecpp0
  libperl5.8 libpng12-0 libpoppler-glib2 libpoppler2 libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpurple0
  libsmbclient libsnmp-base libsnmp10 libss2 libssl0.9.8 libuuid1
  libwnck-common libwnck22 libxfont1 libxml2 libxml2-utils
  linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-image-2.6.22-14-generic linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-common mono-common mono-gac mono-jit mono-runtime
  network-manager openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-style-human openoffice.org-writer openssh-client openssl perl
  perl-base perl-modules pidgin pidgin-data poppler-utils python-bittorrent
  python-gmenu python-libxml2 python-uno samba-common smbclient sound-juicer
  ssh-askpass-gnome tomboy ttf-opensymbol tzdata ubufox xserver-xorg-core
188 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 250Mo dans les archives.
Après dépaquetage, 10,7Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? ATTENTION : les paquets suivants n'ont pas été authentifiés.
  libc6 libc6-i686 findutils libdb4.4 language-pack-en language-pack-fr
  language-pack-gnome-en language-pack-gnome-fr tzdata libisc32 libdns32
  libisccc30 libisccfg30 libbind9-30 liblwres30 bind9-host dnsutils
  app-install-data-commercial apturl avahi-autoipd libavahi-common-data
  libavahi-common3 libavahi-core5 avahi-daemon bittorrent python-bittorrent
  capplets-data libpango1.0-common libpango1.0-0 libgnomeui-common
  libgnomeui-0 libgnome-desktop-2 libedataserver1.2-9 libcamel1.2-10
  libebook1.2-9 libgnome-menu2 libpanel-applet2-0 gnome-menus python-gmenu
  gnome-desktop-data gnome-control-center libgnome-window-settings1
  libwnck-common libwnck22 libavahi-client3 libavahi-compat-libdnssd1
  libcupsys2 libcupsimage2 libgs8 ghostscript cupsys-common cupsys cupsys-bsd
  cupsys-client deskbar-applet eog ghostscript-x evince libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13
  evolution-data-server evolution-data-server-common libedataserverui1.2-8
  libexchange-storage1.2-3 libgtkhtml3.14-19 libnm-glib0 evolution
  evolution-common gtkhtml3.14 evolution-plugins file-roller foo2zjs gcalctool
  gdm gnome-session libgtksourceview2.0-common libgtksourceview2.0-0
  gedit-common gedit libgimp2.0 gimp-python gimp gimp-data gnome-about
  gnome-games gnome-games-data gnome-cards-data gnome-panel-data gnome-panel
  gnome-system-monitor gtk2-engines hwdb-client-common hwdb-client-gnome
  libavahi-glib1 libnm-util0 linux-restricted-modules-common
  linux-restricted-modules-2.6.22-14-generic network-manager
  openoffice.org-calc python-uno openoffice.org-writer openoffice.org-impress
  openoffice.org-draw openoffice.org-style-human openoffice.org-common
  openoffice.org-java-common openoffice.org-base openoffice.org-gtk
  openoffice.org-gnome openoffice.org-evolution openoffice.org-math
  ttf-opensymbol openoffice.org openoffice.org-core sound-juicer ubufox
  gnome-system-tools
Faut-il installer ces paquets sans vérification (o/N) ? 
```

---

### Post by S4nt4 on 2008-02-09
You said update !
Sorry, here it is:

```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-fr
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-fr
Réception de : 1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-fr
Ign http://security.ubuntu.com gutsy-security/restricted Translation-fr
Réception de : 2 http://fr.archive.ubuntu.com gutsy Release.gpg [191B]
Atteint http://fr.archive.ubuntu.com gutsy/main Translation-fr
Ign http://security.ubuntu.com gutsy-security/universe Translation-fr
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-fr
Atteint http://fr.archive.ubuntu.com gutsy/restricted Translation-fr
Atteint http://fr.archive.ubuntu.com gutsy/universe Translation-fr
Atteint http://fr.archive.ubuntu.com gutsy/multiverse Translation-fr
Réception de : 3 http://fr.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://fr.archive.ubuntu.com gutsy-updates/main Translation-fr
Ign http://fr.archive.ubuntu.com gutsy-updates/restricted Translation-fr
Ign http://fr.archive.ubuntu.com gutsy-updates/universe Translation-fr
Ign http://fr.archive.ubuntu.com gutsy-updates/multiverse Translation-fr
Atteint http://security.ubuntu.com gutsy-security Release
Atteint http://fr.archive.ubuntu.com gutsy Release
Atteint http://fr.archive.ubuntu.com gutsy-updates Release
Atteint http://security.ubuntu.com gutsy-security/main Packages
Atteint http://fr.archive.ubuntu.com gutsy/main Packages
Atteint http://fr.archive.ubuntu.com gutsy/restricted Packages
Atteint http://security.ubuntu.com gutsy-security/restricted Packages
Atteint http://security.ubuntu.com gutsy-security/main Sources
Atteint http://security.ubuntu.com gutsy-security/restricted Sources
Atteint http://fr.archive.ubuntu.com gutsy/main Sources
Atteint http://security.ubuntu.com gutsy-security/universe Packages
Atteint http://security.ubuntu.com gutsy-security/universe Sources
Atteint http://security.ubuntu.com gutsy-security/multiverse Packages
Atteint http://security.ubuntu.com gutsy-security/multiverse Sources
Atteint http://fr.archive.ubuntu.com gutsy/restricted Sources
Atteint http://fr.archive.ubuntu.com gutsy/universe Packages
Atteint http://fr.archive.ubuntu.com gutsy/universe Sources
Atteint http://fr.archive.ubuntu.com gutsy/multiverse Packages
Atteint http://fr.archive.ubuntu.com gutsy/multiverse Sources
Atteint http://fr.archive.ubuntu.com gutsy-updates/main Packages
Atteint http://fr.archive.ubuntu.com gutsy-updates/restricted Packages
Atteint http://fr.archive.ubuntu.com gutsy-updates/main Sources
Atteint http://fr.archive.ubuntu.com gutsy-updates/restricted Sources
Atteint http://fr.archive.ubuntu.com gutsy-updates/universe Packages
Atteint http://fr.archive.ubuntu.com gutsy-updates/universe Sources
Atteint http://fr.archive.ubuntu.com gutsy-updates/multiverse Packages
Atteint http://fr.archive.ubuntu.com gutsy-updates/multiverse Sources
3o réceptionnés en 1s (2o/s)
Lecture des listes de paquets...
```

---

### Post by S4nt4 on 2008-02-09
The pb stopped at the 5th or 6th apt-get upgrade...

Very strange, but thx anyway for your quick answers...

---

