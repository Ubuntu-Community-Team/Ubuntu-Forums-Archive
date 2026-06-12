---
title: "Lucid source list"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by jackal_79 on 2010-05-28
Hi! I have recently upgraded my ubuntu to lucid.Can anyone advice on most common and useful sourcelist to be added.I have added some after searching the net.But i don't know if it is required or not.Iam attching my current source list:
*********************************************************
cat /etc/apt/sources.list
# added by the release upgrader
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted

# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1)]/ jaunty main restricted
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid main restricted
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates main restricted
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid universe
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid universe
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates universe
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid multiverse
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid multiverse
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates multiverse
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security main restricted
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security main restricted
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security universe
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security universe
deb [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security multiverse
deb-src [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid-security multiverse


deb [http://ppa.launchpad.net/norsetto/ppa/ubuntu](http://ppa.launchpad.net/norsetto/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) lucid main
deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
***********************************************************

---

### Post by mac9416 on 2010-05-28
> But i don't know if it is required or not.

Technically, no sources are required. But practically speaking, you can get most everything you'll want with the main repositories (which you already have enabled). 

Most applications which require extra sources will offer instructions on how to enable them. Until you need to install a particular application, there's no need to enable the source.

---

