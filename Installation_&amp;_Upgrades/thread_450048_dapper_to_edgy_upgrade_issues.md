---
title: "dapper to edgy upgrade issues"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by UncleO on 2007-05-20
hey everyone i was trying to uprade to edgy from dapper.  and during the upraged process i get this any help would be great.

> Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

---

### Post by mitch.c on 2007-05-22
> **UncleO said:**
> hey everyone i was trying to uprade to edgy from dapper.  and during the upraged process i get this any help would be great.
It looks like you have a repository for the Listen music player in /etc/apt/sources.list. I checked out the url, and it is in fact defunct. Listen is available in the official Edgy repository, so delete the entry from sources.list. Don't forget to:
```
$ sudo apt-get update
```
Cheers
-- 
Mitch

---

