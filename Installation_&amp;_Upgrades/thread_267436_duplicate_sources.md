---
title: "duplicate sources"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by hudelfa on 2006-09-28
Hi everybody,

When I want to update my ubuntu dapper from console (apt-get update) it fetches packests but at the end it gives an error.

Output of the command that I wrote above is;

root@sony-vaio:~# apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get: 3 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 4 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release
Get: 5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 7 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports Release [23.3kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [50.5kB]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Packages
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Sources
Hit [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Sources
Get: 9 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/main Packages [7276B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Get: 10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get: 11 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
Get: 12 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/universe Packages [13.9kB]
Get: 13 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/multiverse Packages [1130B ]
Get: 14 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/main Sources [3510B]
Get: 15 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get: 16 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/universe Sources [5750B]
Get: 17 [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-backports/multiverse Sources [653B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Get: 18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4496B]
Get: 19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [12.4kB]
Get: 20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [960B]
Get: 21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2159B]
Get: 22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [20.8kB]
Get: 23 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get: 24 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]
Get: 25 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [1906B]
Fetched 185kB in 5s (32.5kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/mult iverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-up dates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/univ erse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-upda tes_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


HOW CAN I FIX THIS PROBLEM.

THANKS IN ADVANCE :))

---

### Post by aysiu on 2006-09-28
```
sudo nano -B /etc/apt/sources.list
``` and delete (Control-K) the duplicate entries. Then save (Control-X, Y, Enter).

Alternatively, just [get a fresh sources.list](http://www.psychocats.net/ubuntu/sources).

---

