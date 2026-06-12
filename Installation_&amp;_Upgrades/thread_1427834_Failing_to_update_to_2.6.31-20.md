---
title: "Failing to update to 2.6.31-20"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Fiahhh on 2010-03-12
For a good week now I have gotten some unusual 400: Bad Request errors when trying to install the new kernel. I've tried changing the download server, which hasn't helped. Whenever I reload, I also get Bad Request errors while the package manager tries to decide what should be updated from the new server. It also seems as though half the time, Ubuntu has no updates, while at other times it does. Every other day or so it tells me I have updates, so I try to update and fail, wake up the next day and no updates, yet after that, the same updates I failed to install are back again.

Log from sudo apt-get update:

```

Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-security Release.gpg
Ign http://us.archive.ubuntu.com karmic-security/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic-security Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Ign http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Get:1 http://us.archive.ubuntu.com karmic/universe Packages [5,133kB]
Ign http://us.archive.ubuntu.com karmic/universe Packages
Ign http://us.archive.ubuntu.com karmic/universe Sources
Ign http://us.archive.ubuntu.com karmic/multiverse Packages
Ign http://us.archive.ubuntu.com karmic/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-updates/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Sources
Ign http://us.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://us.archive.ubuntu.com karmic-updates/universe Packages
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-security/main Packages
Ign http://us.archive.ubuntu.com karmic-security/restricted Packages
Ign http://us.archive.ubuntu.com karmic-security/main Sources
Ign http://us.archive.ubuntu.com karmic-security/restricted Sources
Ign http://us.archive.ubuntu.com karmic-security/universe Packages
Ign http://us.archive.ubuntu.com karmic-security/universe Sources
Ign http://us.archive.ubuntu.com karmic-security/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-security/multiverse Sources
Ign http://us.archive.ubuntu.com karmic/restricted Packages
Ign http://us.archive.ubuntu.com karmic/universe Packages
Ign http://us.archive.ubuntu.com karmic/universe Sources
Ign http://us.archive.ubuntu.com karmic/multiverse Packages
Ign http://us.archive.ubuntu.com karmic/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-updates/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Sources
Ign http://us.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://us.archive.ubuntu.com karmic-updates/universe Packages
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-security/main Packages
Ign http://us.archive.ubuntu.com karmic-security/restricted Packages
Ign http://us.archive.ubuntu.com karmic-security/main Sources
Ign http://us.archive.ubuntu.com karmic-security/restricted Sources
Ign http://us.archive.ubuntu.com karmic-security/universe Packages
Ign http://us.archive.ubuntu.com karmic-security/universe Sources
Ign http://us.archive.ubuntu.com karmic-security/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-security/multiverse Sources
Err http://us.archive.ubuntu.com karmic/restricted Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/universe Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/universe Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/multiverse Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/multiverse Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/main Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/restricted Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/main Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/restricted Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/universe Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/universe Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/multiverse Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/multiverse Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/main Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/restricted Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/main Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/restricted Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/universe Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/universe Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/multiverse Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-security/multiverse Sources
  400  Bad Request
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  400  Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

```sources.list file:

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse

```sudo apt-get autoclean:

```

Reading package lists...
Building dependency tree...
Reading state information...
Del gcalctool 5.28.2-0ubuntu2 [205kB]
Del ghex 2.24.0-1 [942kB]
Del apache2-mpm-prefork 2.2.12-1ubuntu2.2 [2,376B]
Del apache2.2-common 2.2.12-1ubuntu2.2 [285kB]
Del apache2.2-bin 2.2.12-1ubuntu2.2 [1,309kB]
Del linux-image-2.6.31-20-generic 2.6.31-20.57 [3,014kB]
Del gnome-screensaver 2.28.0-0ubuntu3.5 [1,196kB]

```

---

### Post by Fiahhh on 2010-03-15
Lalala...

---

### Post by Fiahhh on 2010-03-16
This is frustrating. I can't update, nor can I apt-get install much of anything either. I can obviously connect to the internet, and download files through a web browser, but fail at downloading packages through the update manager.

sudo apt-get update:

```

Ign http://mira.sunsite.utk.edu karmic Release.gpg
Ign http://mira.sunsite.utk.edu karmic/main Translation-en_US
Ign http://mira.sunsite.utk.edu karmic/restricted Translation-en_US
Ign http://mira.sunsite.utk.edu karmic/universe Translation-en_US
Ign http://mira.sunsite.utk.edu karmic/multiverse Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-updates Release.gpg
Ign http://mira.sunsite.utk.edu karmic-updates/main Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-updates/restricted Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-updates/universe Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-updates/multiverse Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-security Release.gpg
Ign http://mira.sunsite.utk.edu karmic-security/main Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-security/restricted Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-security/universe Translation-en_US
Ign http://mira.sunsite.utk.edu karmic-security/multiverse Translation-en_US
Ign http://mira.sunsite.utk.edu karmic Release
Ign http://mira.sunsite.utk.edu karmic-updates Release
Ign http://mira.sunsite.utk.edu karmic-security Release
Ign http://mira.sunsite.utk.edu karmic/main Packages
Ign http://mira.sunsite.utk.edu karmic/restricted Packages
Ign http://mira.sunsite.utk.edu karmic/main Sources
Ign http://mira.sunsite.utk.edu karmic/restricted Sources
Ign http://mira.sunsite.utk.edu karmic/universe Packages
Ign http://mira.sunsite.utk.edu karmic/universe Sources
Ign http://mira.sunsite.utk.edu karmic/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic/multiverse Sources
Ign http://mira.sunsite.utk.edu karmic-updates/main Packages
Ign http://mira.sunsite.utk.edu karmic-updates/restricted Packages
Ign http://mira.sunsite.utk.edu karmic-updates/main Sources
Ign http://mira.sunsite.utk.edu karmic-updates/restricted Sources
Ign http://mira.sunsite.utk.edu karmic-updates/universe Packages
Ign http://mira.sunsite.utk.edu karmic-updates/universe Sources
Ign http://mira.sunsite.utk.edu karmic-updates/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic-updates/multiverse Sources
Ign http://mira.sunsite.utk.edu karmic-security/main Packages
Ign http://mira.sunsite.utk.edu karmic-security/restricted Packages
Ign http://mira.sunsite.utk.edu karmic-security/main Sources
Ign http://mira.sunsite.utk.edu karmic-security/restricted Sources
Ign http://mira.sunsite.utk.edu karmic-security/universe Packages
Ign http://mira.sunsite.utk.edu karmic-security/universe Sources
Ign http://mira.sunsite.utk.edu karmic-security/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic-security/multiverse Sources
Ign http://mira.sunsite.utk.edu karmic/main Packages
Ign http://mira.sunsite.utk.edu karmic/restricted Packages
Ign http://mira.sunsite.utk.edu karmic/main Sources
Ign http://mira.sunsite.utk.edu karmic/restricted Sources
Ign http://mira.sunsite.utk.edu karmic/universe Packages
Ign http://mira.sunsite.utk.edu karmic/universe Sources
Ign http://mira.sunsite.utk.edu karmic/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic/multiverse Sources
Ign http://mira.sunsite.utk.edu karmic-updates/main Packages
Ign http://mira.sunsite.utk.edu karmic-updates/restricted Packages
Ign http://mira.sunsite.utk.edu karmic-updates/main Sources
Ign http://mira.sunsite.utk.edu karmic-updates/restricted Sources
Ign http://mira.sunsite.utk.edu karmic-updates/universe Packages
Ign http://mira.sunsite.utk.edu karmic-updates/universe Sources
Ign http://mira.sunsite.utk.edu karmic-updates/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic-updates/multiverse Sources
Ign http://mira.sunsite.utk.edu karmic-security/main Packages
Ign http://mira.sunsite.utk.edu karmic-security/restricted Packages
Ign http://mira.sunsite.utk.edu karmic-security/main Sources
Ign http://mira.sunsite.utk.edu karmic-security/restricted Sources
Ign http://mira.sunsite.utk.edu karmic-security/universe Packages
Ign http://mira.sunsite.utk.edu karmic-security/universe Sources
Ign http://mira.sunsite.utk.edu karmic-security/multiverse Packages
Ign http://mira.sunsite.utk.edu karmic-security/multiverse Sources
Err http://mira.sunsite.utk.edu karmic/main Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/restricted Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/main Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/restricted Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/universe Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/universe Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/multiverse Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic/multiverse Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/main Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/restricted Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/main Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/restricted Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/universe Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/universe Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/multiverse Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-updates/multiverse Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/main Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/restricted Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/main Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/restricted Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/universe Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/universe Sources
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/multiverse Packages
  400  Bad Request
Err http://mira.sunsite.utk.edu karmic-security/multiverse Sources
  400  Bad Request

```

Thanks for all the help guys.

---

### Post by Fiahhh on 2010-03-17
Alright then. I'll solve the ******* problem myself.

---

