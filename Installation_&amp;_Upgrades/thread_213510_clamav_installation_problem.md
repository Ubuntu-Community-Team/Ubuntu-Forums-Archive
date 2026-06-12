---
title: "clamav installation problem"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by comee on 2006-07-11
I have problem installing clamav.

[INDENT]root@cic:~# apt-get update
Get:1 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper Release [34.8kB]
Get:4 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:5 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/main Packages [619kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [28.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4558B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [7406B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:12 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:13 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/main Sources [255kB]
Get:14 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:15 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/main Packages [41.8kB]
Get:16 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:17 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/main Sources [24.5kB]
Get:18 [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Fetched 1086kB in 1m49s (9920B/s)
Reading package lists... Done
root@cic:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@cic:~# apt-get install clamav
Reading package lists... Done
Building dependency tree... Done
Package clamav is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package clamav has no installation candidate
[/INDENT]

---

