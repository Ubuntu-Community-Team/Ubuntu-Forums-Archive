---
title: "Malformed Source line in completed upgrade to Lucid?"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-02-25
Could not initialize the package information
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 37 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Which did I uncomment out wrongly?  

###### Ubuntu Karmic CD ROM
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#### Ubuntu Update Repository
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-updates main universe multiverse restricted
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-updates main universe multiverse restricted
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-security main universe multiverse restricted
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-security main universe multiverse restricted

#### Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid-security partner


###### Ubuntu Lucid Main
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse

###### Ubuntu Lucid Update
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-updates restricted multiverse

###### Ubuntu Lucid Security
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse

###### Ubuntu Lucid Backports
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

###### Ubuntu Lucid Partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

#### Ubuntuzilla - [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/apt) all main disabled on upgrade to lucid

#### Abiword 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
deb [http://ppa.launchpad.net/abiword-stable/ubuntu](http://ppa.launchpad.net/abiword-stable/ubuntu) lucid main disabled on upgrade to lucid

#### Ubuntu Tweak
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) lucid main disabled on upgrade to lucid

## Chromium Daily Build PPA
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main disabled on upgrade to lucid
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main disabled on upgrade to lucid


## Fabien Tasin PPA
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main disabled on upgrade to lucid
deb-src [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main disabled on upgrade to lucid


## getdeb.net repo
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps

## Themes du ZgegBlog: Project Bisigi
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main disabled on upgrade to lucid
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main disabled on upgrade to lucid

## Openoffice
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main

## Getdeb
wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

## Firefox
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu) lucid main disabled on upgrade to lucid

## Pidgin
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main disabled on upgrade to lucid

## SMPlayer/MPlayer Core Libraries
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A7E13D78E4A4F4F4
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
C20FEBDE130B2A5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0893DC134548A28D
deb [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) lucid main multiverse universe restricted disabled on upgrade to lucid
deb-src [http://ppa.launchpad.net/brandonsnider/ppa/ubuntu](http://ppa.launchpad.net/brandonsnider/ppa/ubuntu) lucid main multiverse universe restricted disabled on upgrade to lucid
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 015A66E603E02400

## Terminator
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb [http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu](http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu) lucid main

## Breathe Icon Set
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu) lucid main disabled on upgrade to lucid

## Playdeb
wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

## Ubuntu Tweak
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main multiverse restricted universe disabled on upgrade to lucid
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main multiverse restricted universe disabled on upgrade to lucid
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2E183FA1E260F5B0

## Mozilla Daily Build Team
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9BDB3D89CE49EC21
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A6DCF7707EBC211F
gpg --keyserver subkeys.pgp.net --recv-key 247510BE && gpg --armor --export  247510BE | sudo apt-key add -
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe


deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) karmic main
deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main
deb [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ailurus/ppa/ubuntu](http://ppa.launchpad.net/ailurus/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) lucid main
deb [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/chromium-daily/beta/ubuntu](http://ppa.launchpad.net/chromium-daily/beta/ubuntu) lucid main

---

### Post by VMC on 2010-02-25
It told you on the error message. Line #37:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```

---

### Post by sports fan Matt on 2010-02-25
So far even with that one hiccup, things are going well.  :)

---

