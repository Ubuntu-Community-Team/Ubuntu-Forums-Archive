---
title: "Lubuntu networkmanager openconnect needs KDE to install?  Ubuntu nmo doesn't??"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by Anaximander Thales on 2015-03-06
In taking a look at [NetworkManager-OpenConnect-gnome]("http://packages.ubuntu.com/utopic/network-manager-openconnect-gnome") details, the dependency list is much different between Ubuntu and Lubuntu.  When I select the noted package, the list of files that is wanting to be installed is this:
```

libkde3support4
ntrack-module-libnl-0
libkrosscore4
libqapt2
libktexteditor4
kdelibs5-data
libkdeui5
libkdeclarative5
kwalletmanager
libthreadweaver4
phonon-backend-gstreamer
kde-runtime
libkparts4
libqca2
libntrack0
kde-runtime-data
libphonon4
libkemoticons4
libkmediaplayer4
libnetworkmanagerqt1
libqt4-qt3support
katepart
libqt4-dbus
libkdnssd4
phonon
libdbusmenu-qt2
libqapt2-runtime
libkatepartinterfaces4
network-manager-openconnect
kdelibs5-plugins
phonon-backend-gstreamer-common
libqtwebkit4
libkjsapi4
libkactivities6
libknewstuff3-4
kdoctools
sgml-data
libkxmlrpcclient4
plasma-nm
libkpty4
libkjsembed4
libqt4-designer
libsolid4
libkhtml5
libntrack-qt4-1
libkfile4
icoutils
libmodemmanagerqt1
libattica0.4
libkdesu5
libdlrestrictions1
libstreams0
libknotifyconfig4
docbook-xml
network-manager-openconnect-gnome
libkdecore5
kdelibs-bin
libkactivities-bin
plasma-scriptengine-javascript
qapt-batch
libstreamanalyzer0
docbook-xsl
libkntlm4
libkdewebkit5
libkcmutils4
libpolkit-qt-1-1
libkubuntu0
libkio5
kate-data
kubuntu-debug-installer
libplasma3

```

Interestingly enough, every other networkmanager-*-gnome package installs the same packages I see listed in their respective details package.  I'm not sure I see why all of the KDE packages are required for Lubuntu and not for ubuntu, and if I'm remembering correclty not for xubuntu either.  Even looking at the Arch distribution, nm-openconnect doesn't require any KDE packages.

Am I missing something?

---

### Post by Anaximander Thales on 2015-03-07
Got it figured out -- after spending hours digging looking for an answer.  At some point, synaptic was set to install all recommends. Plasma-nm (which is recommended) being a KDE package required the above list.  Unchecked it (and actually had to reload) and the KDE applications are no longer selected.

---

### Post by v3.xx on 2015-03-07
Good find.

I have package installs that do the same and I thought it was Qt.  I have noticed that packages with Qt tend to pull in other kde packages.  Now I need to take a closer look at the recommends.

---

