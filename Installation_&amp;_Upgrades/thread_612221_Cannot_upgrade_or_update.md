---
title: "Cannot upgrade or update"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by tobyheath on 2007-11-13
I'm having trouble upgrading and updating Dapper Drake.  Everything it tries to retrieve says '403 Forbidden'
Means I can't install any applications, update any software, or upgrade...

---

### Post by taurus on 2007-11-13
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```
Then, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by tobyheath on 2007-11-13
From sudo apt-get update

Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Errhttp://gb.archive.ubuntu.com dapper/main Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper/restricted Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper/main Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  403 Forbidden
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

(always 403 Forbidden...)

/etc/apt/sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2007-11-13
Is your network working or are you running a proxy?

---

### Post by tobyheath on 2007-11-13
Network is fine, but it's quite a restricted one.  They're probably blocking my access.

---

### Post by taurus on 2007-11-13
> **tobyheath said:**
> Network is fine, but it's quite a restricted one.  They're probably blocking my access.

Looks that way.  You need to contact your IT.

---

