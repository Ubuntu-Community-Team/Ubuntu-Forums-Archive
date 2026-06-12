---
title: "QT App Dependencies"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2010-04-21
When trying to install kate or amarok a whole bunch of dependencies are brought up that I didn't think were needed. Obviously the various libs are required, but its saying that packagekit, nepomuk, update-manager-kde, etc. are needed. I haven't installed a Qt app in a while, but I don't remember those being required. Are these really needed. Heres the full list it says I need.

```

The following NEW packages will be installed:
  akonadi-server exiv2 gdebi-kde icoutils install-package kate kdebase-runtime
  kdebase-runtime-data kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdelibs-bin kdelibs5 kdelibs5-data
  kdepim-runtime kdepimlibs-data kdepimlibs5 kdesudo kpackagekit ksysguardd
  kubuntu-debug-installer libakonadiprivate1 libattica0
  libboost-program-options1.40.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-6
  libiodbc2 libkephal4 libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4
  libpackagekit-glib2-12 libpackagekit-qt-12 libphonon4
  libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasma3
  libplasmaclock4 libplasmagenericshell4 libpolkit-qt-1-0 libprocesscore4
  libprocessui4 libqca2 libqimageblitz4 libqt4-assistant libqt4-help
  libqt4-opengl libqt4-scripttools libqt4-test libqt4-webkit
  libqt4-xmlpatterns libsolidcontrol4 libsolidcontrolifaces4 libsoprano4
  libssh-4 libstreamanalyzer0 libstreams0 libtaskmanager4 libweather-ion4
  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console
  libxine1-misc-plugins libxine1-x mysql-client-core-5.1 mysql-server-core-5.1
  oxygen-icon-theme packagekit packagekit-backend-apt phonon
  phonon-backend-xine plasma-dataengines-workspace
  plasma-scriptengine-javascript plasma-widgets-workspace polkit-kde-1
  python-kde4 python-packagekit python-qt4 python-sip
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu
  ttf-dejavu-extra update-manager-kde virtuoso-nepomuk

```

---

### Post by mc4man on 2010-04-21
It's probably due to all the recommends which are installed by default.

I've no use for amarok 2, (use pana), so can't say if any of those reco's are needed.
You could start with this and add any additional if needed (you have the list or ck. after install in synaptic if need be.

```
sudo apt-get --no-install-recommends install amarok
```

---

### Post by cristianfere on 2010-04-21
Because kate and Amarok is not only a Qt app, but a KDE apps. VLC Media Player, Skype, Opera, Virtual Box and other are a true Qt apps and requires few libs for run, and have a good integration in any desktop environment.

---

### Post by HalfEmptyHero on 2010-04-22
> **cristianfere said:**
> Because kate and Amarok is not only a Qt app, but a KDE apps. VLC Media Player, Skype, Opera, Virtual Box and other are a true Qt apps and requires few libs for run, and have a good integration in any desktop environment.

Thats what I thought. Is there anyway to install just kate, without the kde deps?

---

### Post by ranch hand on 2010-04-22
> **HalfEmptyHero said:**
> Thats what I thought. Is there anyway to install just kate, without the kde deps?
Why?  Just curious, gedit works fine.

---

### Post by HalfEmptyHero on 2010-04-22
Among other things, I like the way kate handles split screens. In gedit you can use the splitview2 plugin, but it isn't as good as kate is by default.

---

### Post by ranch hand on 2010-04-22
Just wondered.  I don't use a slit screen, never thought about it.  Might be handy.  Might have to look at  kate myself.

I have used it but it was on Kubuntu and I am not compatible with KDE.  Kate was one of the few apps that I found to be nice to use on there.

---

### Post by cristianfere on 2010-04-22
> **HalfEmptyHero said:**
> Thats what I thought. Is there anyway to install just kate, without the kde deps?

No. But if you have space on HD, some libs more no make difference.

Or try geany, it has a good split window plugin.

---

