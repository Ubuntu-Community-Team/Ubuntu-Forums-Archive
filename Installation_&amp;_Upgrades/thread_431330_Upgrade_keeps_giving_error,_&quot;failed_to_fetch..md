---
title: "Upgrade keeps giving error, &quot;failed to fetch...&quot;"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2007-05-02
Hey folks!
I'm trying to upgrade from dapper to edgy, THEN to Feisty.
I keep getting the error:
> 
"Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz](http://archive.ubuntu.com/ubuntu/dis...64/Packages.gz) Sub-process gzip returned an error code (1)"
I'm running an HP a1250n with an athlon 64 bit dual core processor with 2gb of ram. I dual boot to windows xp using grub, and I'm running 64 bit dapper on my machine. I'm trying to upgrade to edgy then to feisty rather than load feisty directly in order not to lose "things".

Here is my /etc/apt/sources.list:
> 
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper misc

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END
Any idea's?
Thanks!

---

### Post by randell6564 on 2007-05-03
"bump"

---

### Post by zvacet on 2007-05-03
```
sudo aptitude update && sudo aptitude upgrade
```

I try go to that page and get 404 error.Not found.

---

