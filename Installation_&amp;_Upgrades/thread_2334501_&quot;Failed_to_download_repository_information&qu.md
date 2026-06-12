---
title: "&quot;Failed to download repository information&quot; Error"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by RJLiberator on 2016-08-20
I am trying to solve the problem "Failed to download repository information".

I need to solve this problem to update my drivers for my GPU (NVIDIA GTX 1060).

contents of /etc/apt/sources.list

```
deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

---

### Post by RJLiberator on 2016-08-20
[https://itsfoss.com/failed-to-download-repository-information-ubuntu-13-04/](https://itsfoss.com/failed-to-download-repository-information-ubuntu-13-04/)

So I followed the instructions in this link and now the "Failed to download..." error seems to be fixed. The software updater states that I am up to date, but when I run additional drivers, I still don't see my GTX 1060 driver.

I fresh installed from a USB device.

---

