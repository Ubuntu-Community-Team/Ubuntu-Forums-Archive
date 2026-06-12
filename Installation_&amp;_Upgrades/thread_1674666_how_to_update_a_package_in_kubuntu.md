---
title: "how to update a package in kubuntu"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by mahmoodn on 2011-01-24
I disabled all apt repositories and add only ```
ppa:kubuntu-ppa/beta
```
That repository contains Kdevelop 4.1.90 and I installed 4.1.1 before. Now how can I update that in kubuntu 10.10?

---

### Post by sikander3786 on 2011-01-24
Do you mean you want to update your repository index so that the software from that PPA shows up in Software Center, Synaptic etc? If yes, run this command.

```
sudo apt-get update
```

Make sure there are no errors. If there are some, please post them. If none, you are good to go.

---

### Post by mahmoodn on 2011-01-24
No I didn't mean that. I ran that commands several times. What I am looking is where/how I can tell apt-get to update kdevelop 4.1.1 to 4.1.90.

---

### Post by sikander3786 on 2011-01-24
Update Manager should list any updates for your Software. If that doesn't, did you try this command?

```
sudo apt-get upgrade
```

---

### Post by mahmoodn on 2011-01-24
Thanks, it is listed under "upgrade"
```
mahmood@localhost:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  akonadi-server akregator amarok amarok-common amarok-utils ark dolphin dragonplayer gwenview k3b k3b-data
  kaddressbook kate kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-runtime kdebase-workspace
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins
  kdelibs-bin kdelibs5 kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd kdepim-groupware
  kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-kio-plugins **[COLOR="Red"]kdevelop [/COLOR]**kdm
  kdoctools kfind khelpcenter4 kinfocenter klipper kmail knotes konsole kontact kopete korganizer kpackagekit
  kppp krdc krfb ksnapshot ksysguard ksysguardd ktimetracker libakonadi-contact4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libk3b6 libkabc4 libkatepartinterfaces4 libkblog4 libkcal4 libkcddb4
  libkde3support4 libkdecorations4 libkdecore5 libkdepim4 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkfile4 libkholidays4 libkhtml5 libkimap4 libkimproxy4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkleo4
  libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkontactinterface4
  libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkpty4 libkresources4
  libkrosscore4 libkrossui4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4 libktexteditor4 libktnef4
  libkunitconversion4 libkutils4 libkwineffects1a libkworkspace4 libkxmlrpcclient4 libmailtransport4
  libmessagecore4 libmessagelist4 libmicroblog4 libmimelib4 libnepomuk4 libnepomukquery4a
  libplasma-geolocation-interface4 libplasma3 libplasmaclock4b libplasmagenericshell4 libprocessui4a
  libqapt-runtime libsolid4 libsolidcontrol4a libsublime2 libsyndication4 libthreadweaver4 okular
  plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook
  plasma-scriptengine-javascript plasma-widget-folderview plasma-widget-kimpanel plasma-widget-quickaccess
  plasma-widgets-addons plasma-widgets-workspace polkit-kde-1 python-kde4 python-qt4 systemsettings
The following packages will be upgraded:
  kamera kcalc kdebase-runtime-data kdegraphics-libs-data kdevelop-data kmag kmix kmousetool krosspython
  ksystemlog kwalletmanager libakonadi-kabc4 libattica0 libgpg-error0 libgpgme++2 libkonq5-templates
  libokularcore1 libphonon4 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-0
  libqapt1 libqgpgme1 libqjson0 libsoprano4 okular-extra-backends oxygen-icon-theme oxygen-icon-theme-complete
  phonon phonon-backend-xine plasma-scriptengine-python plasma-widget-kimpanel-backend-ibus policykit-1
  printer-applet python-qt4-dbus python-sip qapt-batch soprano-daemon system-config-printer-kde
40 upgraded, 0 newly installed, 0 to remove and 145 not upgraded.
Need to get 39.0MB/39.1MB of archives.
After this operation, 5,366kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

