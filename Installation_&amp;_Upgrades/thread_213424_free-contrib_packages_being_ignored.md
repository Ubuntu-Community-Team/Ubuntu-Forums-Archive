---
title: "free-contrib packages being ignored"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2006-07-11
Hi all,
        noob here. I just put the following in the /etc/apt/sources.list

```
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

while running apt-get update I get the following output :-
> 
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports/multiverse Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
99% [Connecting to security.ubuntu.com (82.211.81.138)]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [28.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [7406B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [6446B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Fetched 80.3kB in 38s (2068B/s)

 Now look at the ignore statements, why are these archives being ignored. Thnx in advance.

---

### Post by ShirishAg75 on 2006-07-16
just bumping this up, any ideas guys

---

