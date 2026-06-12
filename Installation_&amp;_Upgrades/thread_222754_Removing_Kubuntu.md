---
title: "Removing Kubuntu"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by paparucino on 2006-07-25
Hi guys
Three days ago I asked for a dula boot, someone (thank you GuitarHero) suggest to install kde-destop. I installed it, but I don't like it so I planned to remove it. What me worry is that at boot time the system starts with Kubuntu instead of Ubuntu. Removing kde-dektop causes the reinstallation of Ubuntu? What is the safe way to do it?

thank you in advance.

---

### Post by Ziox on 2006-07-25
> **paparucino said:**
> Hi guys
Three days ago I asked for a dula boot, someone (thank you GuitarHero) suggest to install kde-destop. I installed it, but I don't like it so I planned to remove it. What me worry is that at boot time the system starts with Kubuntu instead of Ubuntu. Removing kde-dektop causes the reinstallation of Ubuntu? What is the safe way to do it?

thank you in advance.

if you want to return to pure gnome (ubuntu) then paste this command:

```
sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder avahi-daemon bogofilter bogofilter-bdb bogofilter-common debtags enscript flac gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kitchensync klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpersonalizer kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt latex-xft-fonts libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-core4 libavahi-qt3-1 libdaemon0 libdbus-qt-1-1c2 libflac++5c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libmodplug0c2 libmpcdec3 libnss-mdns liboggflac3 libopenexr2c2a libpcre3 libpoppler1-qt libpythonize0 libqt-perl libqt3-mt librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libsmokeqt1 libtdb1 libtunepimp2c2a libxcomposite1 libxine-main1 libxvmc1 menu-xdg openoffice.org-kde perl-suid poster postfix procmail psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim speedcrunch ssl-cert vorbis-tools wlassistant
```

The codes is from this site: [http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

---

### Post by paparucino on 2006-07-25
> **Ziox said:**
> if you want to return to pure gnome (ubuntu) then paste this command:
[...]
The codes is from this site: [http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)
Thank you very much.

---

