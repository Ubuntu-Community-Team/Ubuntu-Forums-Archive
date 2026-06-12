---
title: "Update Manager Status Failed"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by andrewabc on 2006-12-01
When I go to system->administration->Update Manager and go into it and check for updates, everyone of them fails to contact the servers.

I'm not sure why it is doing this, has been doing it for about a month now. I think my ISP might be blocking it but not sure how they are (they have some ports blocked etc).

I'm using Dapper 6.06.1

I appear unable to upload to imageshack or anywhere else (crappy internet), Will upload pics them when possible.
I do use automatix, but that shouldn't interfere with regular servers.

Thinking of formatting and installed edgy.

---

### Post by andrewabc on 2006-12-26
I still have this problem. The text when I go into terminal and type sudo apt-get update is:

```
Ign http://people.ubuntu.com ./ Release.gpg
Ign http://archive.canonical.com dapper-commercial Release.gpg
Ign http://people.ubuntu.com ./ Release
Ign http://archive.canonical.com dapper-commercial Release
Ign http://people.ubuntu.com ./ Packages
Ign http://archive.canonical.com dapper-commercial/main Packages
Err http://people.ubuntu.com ./ Packages
  307 Temporary redirect
Err http://archive.canonical.com dapper-commercial/main Packages
  307 Temporary redirect
Ign http://www.getautomatix.com dapper Release.gpg
Ign http://www.getautomatix.com dapper Release
Ign http://www.getautomatix.com dapper/main Packages
Err http://www.getautomatix.com dapper/main Packages
  307 Temporary redirect
Ign http://archive.ubuntu.com dapper Release.gpg
Ign http://archive.ubuntu.com dapper-security Release.gpg
Ign http://archive.ubuntu.com dapper-updates Release.gpg
Ign http://archive.ubuntu.com dapper-backports Release.gpg
Ign http://archive.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/restricted Sources
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://archive.ubuntu.com dapper/universe Sources
Ign http://archive.ubuntu.com dapper/multiverse Packages
Ign http://archive.ubuntu.com dapper/multiverse Sources
Ign http://archive.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper-security/multiverse Packages
Ign http://archive.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-updates/universe Packages
Ign http://archive.ubuntu.com dapper-updates/universe Sources
Ign http://archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://archive.ubuntu.com dapper-updates/multiverse Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/main Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/universe Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/universe Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/main Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/main Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/restricted Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/restricted Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/universe Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/universe Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/multiverse Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-security/multiverse Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/universe Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/universe Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/multiverse Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-updates/multiverse Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  307 Temporary redirect [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-i386/Packages.gz 307 Temporary redirect
Failed to fetch http://people.ubuntu.com/~seb128/deb/./Packages.gz 307 Temporary redirect
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz 307 Temporary redirect
Failed to fetch http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.gz 307 Temporary redirect
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz 307 Temporary redirect [IP: 195.248.90.35 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Is it possible it is not my internet that is not letting it work?
I should know in a week whether it is the internet or not as I am switching ISPs.

---

### Post by ricardisimo on 2006-12-28
I'm getting something similar. Here are the repository indexes that I can't access for some reason:
```
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/source/Sources.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by andrewabc on 2007-01-15
My problem is solved after switching ISPs.
The ISP must have somehow not allowed those types of connections (must not have been normal http port 80 connection).

---

