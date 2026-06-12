---
title: "Doesn't Know I Upgraded"
date: 2017-09-09
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2017-09-09
After upgrading two laptops from 12.04 to 14.04, I still get the following message on login: "This Ubuntu 12.04 LTS system is past its End of Life, and is no longer
receiving security updates. ..."

Not exactly a major problem, but curious.

---

### Post by jeremy31 on 2017-09-09
When did you attempt the upgrade?  Post results for ```
uname -r; cat /etc/lsb-release; cat /etc/apt/sources.list
```

---

### Post by grahammechanical on 2017-09-09
What procedure did you use to "upgrade?"

When a version of Ubuntu reaches end of life (as 12.04 has done) the internet location of the software archives are changed to something like deb: [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) blah blah.

I don't know if this has happened yet to 12.04 but if it has you will need to follow the procedure for doing an End of Life (EOL) upgrade

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Otherwise, you can try doing a regular update/upgrade. That might bring in some updates that have not yet been applied.

Regards.

---

### Post by bilkay on 2017-09-10
> **jeremy31 said:**
> When did you attempt the upgrade?  Post results for ```
uname -r; cat /etc/lsb-release; cat /etc/apt/sources.list
```

```
$ uname -r; cat /etc/lsb-release; cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

```

I just upgraded two laptops a few weeks ago. This is what I see when I log in to either:

```
Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-129-generic i686)

 * Documentation:  https://help.ubuntu.com/

New release '16.04.3 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

This Ubuntu 12.04 LTS system is past its End of Life, and is no longer
receiving security updates.  To protect the integrity of this system, it’s
critical that you enable Extended Security Maintenance updates:
 * https://www.ubuntu.com/esm

No mail.

```

---

### Post by jeremy31 on 2017-09-10
It is a bug that should be fixed shortly in the package ubuntu-advantage-tools it seems there is a file in /etc/update-motd.d/ that has Ubuntu 12.04 hard coded in the file
```
cat /etc/update-motd.d/90-esm
```

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1707290](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1707290) shows that the fix was released just a couple days ago so it may or not be in the repos yet

---

### Post by bilkay on 2017-09-10
> **jeremy31 said:**
> It is a bug that should be fixed shortly in the package ubuntu-advantage-tools it seems there is a file in /etc/update-motd.d/ that has Ubuntu 12.04 hard coded in the file
```
cat /etc/update-motd.d/90-esm
```

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1707290](https://bugs.launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bug/1707290) shows that the fix was released just a couple days ago so it may or not be in the repos yet

Thanks!

---

