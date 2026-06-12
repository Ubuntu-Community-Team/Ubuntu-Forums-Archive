---
title: "upgrade error"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by smokiedbest on 2007-06-03
i am tryin to upgrade from dapper to edgy but aftersome time it brings up this error:

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1) 
can anyone help me out here

---

### Post by taurus on 2007-06-03
How do you try to upgrade from dapper to edgy?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by smokiedbest on 2007-06-03
i tried upgrading by doing
$gksu "update-manager -c"


here is the result of cat /etc/apt/sources.list

# deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

