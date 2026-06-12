---
title: "cannot update my system"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by wishartz on 2006-10-12
I updated my system last night, for the first time in months. Now I can no longer update my system.  I get this message:

ubuntuwish@ubuntuwish-laptop:~$ sudo apt-get update
Get: 1 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Get: 2 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 4 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Get: 5 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Errhttp://packages.freecontrib.org dapper Release

Get: 9 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Fetched 9648B in 2s (4048B/s)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
ubuntuwish@ubuntuwish-laptop:~$


I have tried looking for similar posts on this, or how I can get the public key it is missing.  Does anybody know how I can fix this.  This all started when it updated compiz, no I cannot even remove the package or update it.

Any help would be greatly appreciated.

---

### Post by Kateikyoushi on 2006-10-12
Copy these to the terminal and it solves the key problem.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

### Post by wishartz on 2006-10-12
Thats fixed it.  Thanks.

---

