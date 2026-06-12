---
title: "Where adobeflash-plugin is located?"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by giannisfs on 2009-12-01
I have ubuntu 9.10 64 bit
I have flash installed ( i can see flash pages youtube etc...)
I have the multiverse repository enabled and also the 
restricted extras
**But** i am very curius where is  the adobeflash-plugin
i can't find the package name 
for example i execute
```
sudo apt-get install adobe-flashplugin
```
and it gives me back
```
E: Couldn't find package adobe-flashplugin
```

my sources.list file is contains the following 
```
/etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe



#vlc
deb http://archive.ubuntu.com/ubuntu/ karmic-proposed restricted main universe multiverse



#medibuntu/
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ karmic free non-free


#Virtualbox
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#VLC 
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

```

Does anybody faced the same problem?
I am dying from curiosity
Thanks in advance :D

---

### Post by darkod on 2009-12-01
Depends which one is installed, one is called flashplugin-nonfree

---

### Post by mkvnmtr on 2009-12-01
I believe it is in the partner repository which you need to enable in software sources.

---

