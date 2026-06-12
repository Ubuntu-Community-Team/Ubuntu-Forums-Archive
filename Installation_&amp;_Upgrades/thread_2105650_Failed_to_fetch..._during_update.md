---
title: "Failed to fetch... during update"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by NetJunky on 2013-01-16
I'm using Ubuntu Server 10.10. Recently I added PPA for PhpMyAdmin and ran ```
sudp apt-get update
``` and it worked perfectly fine.

Today I noticed, that PPA got updated, thou I thought of updating and when I tried to run ```
sudp apt-get update
``` it gave a list with lots and lots **Failed to fetch...** lines

Here is my result /etc/apt/sources.list:
```

#
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

```

**P.S.**
I did look through other topics regarding that, but didn't find any obvious solution. Migration to other(newer) version is not an option.

---

### Post by Bashing-om on 2013-01-16
NetJunky; Hi !

I hate to be the harbinger of bad news, but, maverick version 10.10 reached end of life on April 10, 2012. That version is no longer supported.
> Package repositories for old Ubuntu releases are dropped from Ubuntu’s  upstream package repository and are removed from Ubuntu package mirrors.  However, Ubuntu still makes them available here:[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

source:[http://blog.nowherelan.com/2012/01/09/apt-package-resource-list-for-old-ubuntu-releases/](http://blog.nowherelan.com/2012/01/09/apt-package-resource-list-for-old-ubuntu-releases/)

may be of some slight relieve until you can do better.

---

### Post by mörgæs on 2013-01-17
You should consider a fresh install of 12.04 or 12.10. You will have to do a double upgrade in order to reach a supported version (11.10), from which you soon have to upgrade again.

---

