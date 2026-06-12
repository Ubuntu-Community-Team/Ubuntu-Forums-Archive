---
title: "Updating = 403 error"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by hybzik on 2010-01-27
Checking for updates (system->administration->update manager) in 8.04 Hardy returns the message below.
I've checked my network connection is working, checked I'm not using a proxy, and have tried changing servers but always get the same message.
I can't figure out what the problem is or how to fix it. Anybody have an idea?

> Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.13 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/main/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/main/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/restricted/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/restricted/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  403 Forbidden [IP: 130.130.37.13 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/universe/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/universe/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy/multiverse/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/main/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/main/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/main/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/main/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/universe/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Failed to fetch [http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://mirror.pacific.net.au/linux/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  403 Forbidden [IP: 130.130.37.12 8080]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hybzik on 2010-02-24
bump.

anything would be nice.

---

### Post by texaswriter on 2010-02-24
```
sudo aptitude update
sudo aptitude safe-upgrade
```

hope that works. Otherwise, restart computer and try again.

---

