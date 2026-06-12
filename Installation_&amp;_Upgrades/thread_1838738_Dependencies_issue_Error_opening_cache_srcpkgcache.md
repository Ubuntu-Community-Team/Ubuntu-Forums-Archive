---
title: "Dependencies issue? Error opening cache srcpkgcache.bin 13:Permission denied"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by amicable on 2011-09-04
I have a 'no entry' red icon in my status bar which talks about srcpkgcache.bin and indicates I've probably got unmet dependencies. I'd like to have copied the mouse-over error to show you but I don't know how...

Have searched for quite sometime and it seems this error may have has sthg to do with my sources list. I've also tried ```
sudo apt-get install -f
```

Here is my sources.list. Can anyone work out what I'm doing wrong? How do you find out what dependencies haven't been met?

```
# 
# deb cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free
deb http://archive.canonical.com/ lucid partner
```

---

### Post by amicable on 2011-09-06
Can anyone help me? I keep trawling through Google searches on this issue and I'm not getting anywhere :confused:

---

