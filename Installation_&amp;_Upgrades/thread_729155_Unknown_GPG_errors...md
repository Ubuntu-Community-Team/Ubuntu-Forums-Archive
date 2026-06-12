---
title: "Unknown GPG errors..?"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by DirtyMonkey on 2008-03-19
OS: Dapper Drake 6.06 LTS

Can anyone help me resolve the fix errors i get below whicg appeard all of a sudden when I hit reload in Synaptics?

```
[B]W: GPG error: [ftp://archieve.ubuntu.com](ftp://archieve.ubuntu.com) dapper Release: Unknown error executing gpgv
W: GPG error: [ftp://archieve.ubuntu.com](ftp://archieve.ubuntu.com) dapper-security Release: Unknown error executing gpgv[/B]
```

```
cat /etc/apt/sources.list:
```

```
#Host Europe server:
deb ftp://80.237.136.138/mirror/archive.ubuntu.com/ dapper main multiverse universe
deb ftp://80.237.136.138/mirror/archive.ubuntu.com/ dapper-security main restricted universe multiverse

deb ftp://archive.ubuntu.com/ubuntu dapper main multiverse universe
deb ftp://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#AUTOMATIX REPOS END
```

```
apt-get update
```

```
Hit ftp://80.237.136.138 dapper Release.gpg
Hit ftp://80.237.136.138 dapper-security Release.gpg
Get:1 ftp://80.237.136.138 dapper Release [34.8kB]
Get:2 ftp://80.237.136.138 dapper-security Release [50.9kB]
Hit ftp://80.237.136.138 dapper/main Packages
Hit ftp://80.237.136.138 dapper/multiverse Packages
Hit ftp://80.237.136.138 dapper/universe Packages
Hit ftp://80.237.136.138 dapper-security/main Packages
Hit ftp://80.237.136.138 dapper-security/restricted Packages
Hit ftp://80.237.136.138 dapper-security/universe Packages
Hit ftp://80.237.136.138 dapper-security/multiverse Packages
Get:3 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:6 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:7 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Get:8 ftp://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Get:9 ftp://archive.ubuntu.com dapper-security Release.gpg [191B]
Get:10 ftp://archive.ubuntu.com dapper Release [34.8kB]
Get:11 ftp://archive.ubuntu.com dapper-security Release [50.9kB]
Hit ftp://archive.ubuntu.com dapper/main Packages
Hit ftp://archive.ubuntu.com dapper/multiverse Packages
Hit ftp://archive.ubuntu.com dapper/universe Packages
Hit ftp://archive.ubuntu.com dapper-security/main Packages
Get:12 http://www.getautomatix.com dapper Release.gpg [189B]
Hit ftp://archive.ubuntu.com dapper-security/restricted Packages
Hit ftp://archive.ubuntu.com dapper-security/universe Packages
Hit ftp://archive.ubuntu.com dapper-security/multiverse Packages
Hit http://www.getautomatix.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Fetched 172kB in 1s (142kB/s)
Reading package lists... Done
```

Thanks in advance, DM.

---

### Post by DirtyMonkey on 2008-03-21
... Bump ...

---

### Post by squabeggz on 2008-06-11
Try resetting your time and date.  My old Dell laptop won't retain this info anymore. After I got similar errors, I set my clock to the correct time and date and it worked again.

---

