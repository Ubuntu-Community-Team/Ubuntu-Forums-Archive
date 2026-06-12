---
title: "Upgrade 14.04 LTS to 16.04 LTS error"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by zkab on 2016-10-11
I try to upgrade a server 14.04 LTS ->16.04 LTS with 'sudo do-release-upgrade' and get following - can it be ignored ?

```
Unknown Multi-Arch type 'no' for package 'compiz-core'
Unknown Multi-Arch type 'no' for package 'compiz-gnome'
Unknown Multi-Arch type 'no' for package 'libxapian-dev'
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
Unknown Multi-Arch type 'no' for package 'kwin'
Unknown Multi-Arch type 'no' for package 'kwin-dev'
Unknown Multi-Arch type 'no' for package 'kwin-wayland'
Unknown Multi-Arch type 'no' for package 'kwin-x11'
Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
Ignoring Provides line with DepCompareOp for package php-seclib
Ignoring Provides line with DepCompareOp for package php-sabre-http
Ignoring Provides line with DepCompareOp for package php-math-biginteger
Ignoring Provides line with DepCompareOp for package pypy-cffi
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
Unknown Multi-Arch type 'no' for package 'compiz-core'
Unknown Multi-Arch type 'no' for package 'compiz-gnome'
Unknown Multi-Arch type 'no' for package 'libxapian-dev'
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
Unknown Multi-Arch type 'no' for package 'kwin-dev'
Unknown Multi-Arch type 'no' for package 'kwin-wayland'
Unknown Multi-Arch type 'no' for package 'kwin-x11'
Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
Ignoring Provides line with DepCompareOp for package pypy-cffi
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
Unknown Multi-Arch type 'no' for package 'compiz-core'
Unknown Multi-Arch type 'no' for package 'compiz-gnome'
Ignoring Provides line with DepCompareOp for package php-math-biginteger
Ignoring Provides line with DepCompareOp for package pypy-cffi
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
Unknown Multi-Arch type 'no' for package 'compiz-core'
Unknown Multi-Arch type 'no' for package 'compiz-gnome'
Ignoring Provides line with DepCompareOp for package pypy-cffi
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
You may want to run apt-get update to correct these problems
```

My source.list looks like this:

```
cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

#deb cdrom:[Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.cat /etc/apt/sources.list
# 

# deb cdrom:[Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

#deb cdrom:[Ubuntu-Server 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```

---

### Post by ajgreeny on 2016-10-11
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by zkab on 2016-10-11
OK - I'll use Code-Tags next time ... it really looks much better.
But what about my problem with the update  ...

---

### Post by zkab on 2016-10-15
Anyone ?

---

