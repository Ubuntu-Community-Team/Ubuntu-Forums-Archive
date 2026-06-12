---
title: "[SOLVED] Apt gets packages that are not required"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by stringkarma on 2008-02-07
Lately I have been seeing that often apt informs me that I need several packages along with the one(s) that I want. I tell it to continue. Then the next time I use apt it says that most if not all of these additional packages are no longer required. 
What's the deal? I haven't seen this before and it has happened several times recently.

---

### Post by stringkarma on 2008-06-01
Bump

---

### Post by Joeb454 on 2008-06-01
What command are you actually using to install stuff?

---

### Post by stringkarma on 2008-06-01
sudo apt-get install <package>

it seems to be mostly documentation or libraries that get downloaded and then immediately become "no longer needed"

oddly it happens far more often on one computer than my others, are there any config files that might be somehow messed up on that comp?

---

### Post by stringkarma on 2008-06-02
ok so here is a prime example. I want to install flashplugin-nonfree and it is going to install and then remove most of KDE (I'm using gnome).

Here is a simulation, notice that it is telling me that the things I WILL install are no longer required ...

```
$ sudo apt-get install -s flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.6++ libktnef1 ksig artsbuilder kleopatra ksvg kdepim-kio-plugins
  atlantikdesigner libkcal2b libqt3-mt-psql libjpeg-progs
  kdeaddons-kfile-plugins kicker-applets kaddressbook libkpimexchange1
  konq-plugins kdepim-kresources kdeaddons-doc-html kworldclock kregexpeditor
  korganizer atlantik akregator ark noatun-plugins libksieve0 kate-plugins
  kdeaddons libkdepim1a noatun knotes libqt3-mt-mysql kaddressbook-plugins
  khelpcenter ttf-xfree86-nonfree kdeartwork-misc xfs libkmime2 libkleopatra1
  libmimelib1c2a libkpimidentities1 kate kmail libkdegames1 libqt3-mt-odbc
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akregator ark artsbuilder atlantik atlantikdesigner kaddressbook
  kaddressbook-plugins kamera kate kate-plugins kcontrol kdeaddons
  kdeaddons-doc-html kdeaddons-kfile-plugins kdeartwork-misc kdebase-bin
  kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a
  kdemultimedia-kio-plugins kdepim-kio-plugins kdepim-kresources kdesktop
  kfind kghostview khelpcenter kicker kicker-applets kleopatra kmail knotes
  konq-plugins konqueror konqueror-nsplugins konsole korganizer kregexpeditor
  ksig ksvg kworldclock libarts1-akode libarts1c2a libavahi-qt3-1 libdb4.6++
  libdbus-qt-1-1c2 libjpeg-progs libkcal2b libkcddb1 libkdegames1 libkdepim1a
  libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1
  libksieve0 libktnef1 libmimelib1c2a libqt3-mt libqt3-mt-mysql libqt3-mt-odbc
  libqt3-mt-psql noatun noatun-plugins pinentry-qt pmount ttf-xfree86-nonfree
  xfs
Suggested packages:
  fam xmms-kde libgcj7-awt libjessie-java
The following NEW packages will be installed:
  akregator ark artsbuilder atlantik atlantikdesigner flashplugin-nonfree
  kaddressbook kaddressbook-plugins kamera kate kate-plugins kcontrol
  kdeaddons kdeaddons-doc-html kdeaddons-kfile-plugins kdeartwork-misc
  kdebase-bin kdebase-bin-kde3 kdebase-data kdebase-kio-plugins kdelibs-data
  kdelibs4c2a kdemultimedia-kio-plugins kdepim-kio-plugins kdepim-kresources
  kdesktop kfind kghostview khelpcenter kicker kicker-applets kleopatra kmail
  knotes konq-plugins konqueror konqueror-nsplugins konsole korganizer
  kregexpeditor ksig ksvg kworldclock libarts1-akode libarts1c2a
  libavahi-qt3-1 libdb4.6++ libdbus-qt-1-1c2 libjpeg-progs libkcal2b libkcddb1
  libkdegames1 libkdepim1a libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libksieve0 libktnef1 libmimelib1c2a libqt3-mt
  libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql noatun noatun-plugins
  pinentry-qt pmount ttf-xfree86-nonfree xfs
0 upgraded, 71 newly installed, 0 to remove and 0 not upgraded.
```

Why?!?

---

### Post by stringkarma on 2008-06-08
In case anyone else has this problem, here is the answer. If you somehow have set your apt.conf file to automatically install packages marked as suggested, it may install them but not think they are necessary.

Change your apt.conf file line that says install suggested to "false"

---

