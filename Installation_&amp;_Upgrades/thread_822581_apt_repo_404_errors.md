---
title: "apt repo 404 errors"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by stairwayoflight on 2008-06-08
Hey all,

Somehow I managed to frack up my apt on eeeXubuntu. (If you don't know, it's almost stock Xubuntu.)

Here is my sources.list:
```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ppa.launchpad.net/avassalotti/ubuntu feisty main

```

Here is the output of 'sudo aptitude update':
```
Ign http://ca.archive.ubuntu.com gutsy Release.gpg
Ign http://ca.archive.ubuntu.com gutsy/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates Release.gpg
Ign http://ca.archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports Release.gpg
Ign http://ca.archive.ubuntu.com gutsy-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy Release
Ign http://ca.archive.ubuntu.com gutsy-updates Release
Ign http://ca.archive.ubuntu.com gutsy-backports Release
Ign http://ca.archive.ubuntu.com gutsy/main Packages
Ign http://ca.archive.ubuntu.com gutsy/restricted Packages
Ign http://ca.archive.ubuntu.com gutsy/main Sources
Ign http://ca.archive.ubuntu.com gutsy/restricted Sources
Ign http://ca.archive.ubuntu.com gutsy/universe Packages
Ign http://ca.archive.ubuntu.com gutsy/universe Sources
Ign http://ca.archive.ubuntu.com gutsy/multiverse Packages
Ign http://ca.archive.ubuntu.com gutsy/multiverse Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/main Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/main Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/universe Packages
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ca.archive.ubuntu.com gutsy-updates/multiverse Sources
Ign http://ca.archive.ubuntu.com gutsy-backports/main Packages
Ign http://ca.archive.ubuntu.com gutsy-backports/restricted Packages
Ign http://ca.archive.ubuntu.com gutsy-backports/universe Packages
Ign http://ca.archive.ubuntu.com gutsy-backports/multiverse Packages
Ign http://ppa.launchpad.net feisty Release.gpg
Ign http://ppa.launchpad.net feisty/main Translation-en_CA
Ign http://ca.archive.ubuntu.com gutsy-backports/main Sources
Ign http://ca.archive.ubuntu.com gutsy-backports/restricted Sources
Ign http://ca.archive.ubuntu.com gutsy-backports/universe Sources
Ign http://ca.archive.ubuntu.com gutsy-backports/multiverse Sources
Err http://ca.archive.ubuntu.com gutsy/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/restricted Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/universe Packages
  404 Not Found
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com gutsy-security Release
Err http://ca.archive.ubuntu.com gutsy/universe Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy/multiverse Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/restricted Sources
  404 Not Found
Hit http://ppa.launchpad.net feisty Release
Err http://ca.archive.ubuntu.com gutsy-updates/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/universe Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-updates/multiverse Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/main Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/restricted Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/universe Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/multiverse Packages
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/main Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/restricted Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/universe Sources
  404 Not Found
Err http://ca.archive.ubuntu.com gutsy-backports/multiverse Sources
  404 Not Found
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://ppa.launchpad.net feisty/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://ppa.launchpad.net feisty/main Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Fetched 1B in 0s (1B/s)
Reading package lists...

```

I believe this is a stock xubuntu sources.list with the minor change I made to add a repo for emacs. Commenting out that entry doesn't help. Now I can't even install emacs from the repos!

---

### Post by bapoumba on 2008-06-08
From a navigator, the .ca repos looks weirdly setup :confused:
Please try another repo (or remove all the .ca in /etc/apt/sources.list), reload the file (sudo aptitude update) and see if it works better.

---

