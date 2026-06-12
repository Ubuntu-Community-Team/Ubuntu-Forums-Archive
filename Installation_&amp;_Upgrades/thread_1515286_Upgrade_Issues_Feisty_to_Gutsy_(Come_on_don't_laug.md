---
title: "Upgrade Issues Feisty to Gutsy (Come on don't laugh;-)"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2010-06-22
Hi All,

been a long time since I played with Ubuntu. I've decided it's time to upgrade. Don't feel like going through a re-install at this stage. I've been following the below URL,

[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)

but getting a lot of the below errors after running the below command,

sudo ./gutsy --frontend DistUpgradeViewText --mode=server


Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz) 404 Not Found


Here are my /etc/hosts and sources.list content.

$ cat /etc/hosts127.0.0.1 localhost marklaptop
127.0.1.1 marklaptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
91.189.88.35    archive.ubuntu.com




$ cat /etc/apt/sources.list
##Acquire::http::Proxy "http://172.31.222.254:3128"
##deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ gutsy main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ursys.archive.ubuntu.com/ubuntu/](http://ursys.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ursys.archive.ubuntu.com/ubuntu/](http://ursys.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main


deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
deb-src [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

Thanks.

Mark

---

### Post by lechien73 on 2010-06-22
The problem is that your sources.list file still contains references to the repositories that were used when Gutsy was "live".

Make a backup of your sources.list file, and then replace the contents of it with the EOL repositories:

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

It's not just a case of adding that to the end of an existing sources.list, but actually replacing it.

Hope that helps :)

---

### Post by wilee-nilee on 2010-06-22
I would do a fresh install even if this works it will take a lot longer then a fresh install, if it doesn't work, well then you have to decide something.

---

### Post by coolboarderguy on 2010-06-22
Ah, yes, I bit the bullet and did the new install. Worth the extra trouble. Thanks.

Mark

---

### Post by coolboarderguy on 2010-06-22
> **lechien73 said:**
> The problem is that your sources.list file still contains references to the repositories that were used when Gutsy was "live".

Make a backup of your sources.list file, and then replace the contents of it with the EOL repositories:

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

It's not just a case of adding that to the end of an existing sources.list, but actually replacing it.

Hope that helps :)

Hi, yes, I ended up working it out. I then just found that it was painful with all the steps required to do it that way. Happy I bothered with the new install. Thanks for assisting.

---

