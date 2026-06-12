---
title: "repository problem"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by terrordrone on 2008-11-26
Hi,

i just happened to recently check pidgin's version. I am still at 2.4.1 while 2.5.2 is released. But synaptic shows no updates. 

I am on Hardy.

This is my sources.list:

```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main



```

---

### Post by Elfy on 2008-11-26
The standard repos will stiil have the old version and it's likely that is the way it will stay - stable and working versions.

If you want the newest version of pidgin you can enable the backports - Software Sources - Update tab it appears that has the newer version

[http://packages.ubuntu.com/hardy-backports/pidgin](http://packages.ubuntu.com/hardy-backports/pidgin)

---

### Post by terrordrone on 2008-11-26
Thanks..  i enabled the backports updates in the synaptic repositories manager.

---

