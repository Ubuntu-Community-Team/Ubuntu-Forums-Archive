---
title: "Trying to upgrade 9.10 via command line, failing hard."
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by Sarteck on 2011-11-23
Yar, I have a few 9.10 servers I am trying to upgrade.  Unfortunately, I'm not doing so well.

```
**sudo apt-get update**
Ign http://security.ubuntu.com karmic-security Release.gpg
Ign http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic-updates Release.gpg
Ign http://security.ubuntu.com karmic-security Release
Ign http://archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://archive.ubuntu.com karmic-updates Release
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Err http://security.ubuntu.com karmic-security/main Packages
  404  Not Found [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Err http://security.ubuntu.com karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/main Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Err http://archive.ubuntu.com karmic/main Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic/restricted Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic/main Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic/restricted Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://security.ubuntu.com karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic/universe Sources
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com karmic-updates/universe Sources
  404  Not Found [IP: 91.189.88.46 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

```
**sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
**sudo nano /etc/apt/sources.list**
## main & restricted repositories
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
#deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted

## universe repositories
deb http://archive.ubuntu.com/ubuntu/ karmic universe
#deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
#deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe

```
(The commented sources are the originals--I tried just leaving the "us." off a few to see if that would work.  It didn't.)


Obviously, no upgrade.  >_>
```
**cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```




Am I doing something wrong, or is it Ubuntu?

---

### Post by Sarteck on 2011-11-24
This thread solved my problem:
[http://ubuntuforums.org/showthread.php?t=1127305](http://ubuntuforums.org/showthread.php?t=1127305)


Basically, replace the subdomains of ubuntu.com with "old-releases"

---

### Post by bzhao on 2012-05-09
"old-releases.ubuntu.com"  is almost the only one site which works for jaunty currently. I have spent serveral hours to see it, because I have been using it to install Java 5 to Ubuntu system. The time is running too fast!!!!

---

