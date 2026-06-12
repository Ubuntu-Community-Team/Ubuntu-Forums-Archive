---
title: "Kubuntu to ubuntu"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by allspiritseve on 2008-04-03
I am looking at possibly switching from kde to gnome... last time I tried to add gnome to my installation, the install couldn't finish because I didn't have enough space on that partition (5gb) for both gnome and kde. I have a 2gb swap partition, I could place that at the end of the drive and expand my primary partition. Will that be enough though? How much extra space will gnome add onto a kde install?

Thanks,

Cory

---

### Post by warp99 on 2008-04-03
If you don't have enough space you can remove KDE first, then install Gnome from the command line. During the Grub boot process press escape then choose recovery mode. While in recovery you can do the following:

```
apt-get remove --purge kubuntu-desktop 
```

then clean any remaining packages to reclaim space:

```
apt-get clean
```

install the gnome-desktop

```
apt-get install gnome-desktop 
```

reboot and you should boot to a nice Ubuntu GDM login. Hope this helps.

Edit:

Before you do this make sure in recovery mode that you have an **established internet connection:**

```
ping -c 10 google.com 
```

---

### Post by zvacet on 2008-04-03
In recovery mode you don´t need sudo.You can do this without going to the recovery mode

```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop
```

---

### Post by warp99 on 2008-04-03
> **zvacet said:**
> In recovery mode you don´t need sudo.You can do this without going to the recovery mode 

You're right about sudo, I forgot about that. Thanks.  :)

I suggested recovery because in the past there have been problems if xserver is loaded with any of the desktop components residing in memory.  I didn't want the original poster to be stuck in the middle of the removal process and something go wrong.

---

