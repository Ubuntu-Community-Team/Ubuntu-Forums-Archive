---
title: "LiVES repository"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by svenskmand on 2008-08-04
anybody knows how to get LiVES in the repository with apt-get?

in this thread [http://ubuntuforums.org/showthread.php?t=94541]("http://ubuntuforums.org/showthread.php?t=94541") they say LiVES is in the repository, but i can't install it, i have enabled all deb ... lines in /etc/apt/sources.list but with no luck :S

this is my /etc/apt/sources.list file

```

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
 deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

# Egne repositorys
deb http://repository.cairo-dock.org/ubuntu hardy cairo-dock

```

Best Regards :)

---

### Post by svenskmand on 2008-08-14
I havn't found a repository but a .deb-file is available at [http://www.getdeb.net/app.php?name=lives]("http://www.getdeb.net/app.php?name=lives").

---

