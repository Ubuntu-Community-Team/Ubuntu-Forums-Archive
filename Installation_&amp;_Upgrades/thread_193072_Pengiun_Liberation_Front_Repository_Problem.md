---
title: "Pengiun Liberation Front Repository Problem"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by J0s3ph on 2006-06-09
Hello

I seem to be having trouble accessing the PLF repositories with APT.

The contents of my sources.list file is...
-
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
-

... and the output from SUDO APT-GET UPDATE is...
-
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Get: 2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get: 4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release
Get: 5 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release.gpg
Get: 6 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Get: 7 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Get: 8 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Get: 9 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources
Get: 10 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Packages
Get: 11 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/free Sources [321B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Get: 12 [ftp://ftp.free.fr](ftp://ftp.free.fr) dapper/non-free Sources [478B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 803B in 10s (74B/s)
Reading package lists... Done
-

I've also tried...
-
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
-

... with the same results. Does anyone know what's going on? :\

Thanks for any help.

-
Joseph

---

