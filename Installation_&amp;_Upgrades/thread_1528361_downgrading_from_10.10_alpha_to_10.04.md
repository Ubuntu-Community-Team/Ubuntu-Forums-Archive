---
title: "downgrading from 10.10 alpha to 10.04"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by pixiesnoot on 2010-07-10
Hello everyone and thanks in advance for helping,

I recently decided to try the ubuntu 10.10 alpha and I'm getting an annoying amount of crash reports, is there an easy way for me to downgrade back to the normal ubuntu without reinstalling the whole os from my disk?

---

### Post by mikewhatever on 2010-07-10
No, there is not. :sad:

---

### Post by pixiesnoot on 2010-07-10
ok, thanks.

---

### Post by k4rshh on 2010-07-21
Have you tried booting with the 10.04 usb disk?

---

### Post by Martiini on 2010-11-28
debian / ubuntu downgrade of packages is fully implemented by apt / aptitude 
explained here [http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

search ubuntu forums for "downgrade"

whoever says debian/ubuntu downgrade "is not possible and not supported" is a downright straight liar
I have done it in Debian and several ubuntu versions
its true, it leaves system in "broken" or "inconsistent" state
Google debian downgrade

you cannot do "apt-get dist-downgrade -t maverick" ... 
but .. 
you edit 2 files:
etc/apt/preferences
etc/apt/sources.list

you call mix of package management commands
aptitude dist-upgrade
apt-get install -f
dpkg -i --force-all <problem package>
dpkg -r --force-all <problem package>

/etc/apt/preferences
```

Package: *
Pin: release a=maverick
Pin-Priority: 1001

Package: *
Pin: release a=natty
Pin-Priority: 60

Package: *
Pin: release a=natty
Pin-Priority: 50

```

/etc/apt/sources.list
```


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe 
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ natty partner 
# deb-src http://archive.canonical.com/ubuntu/ natty partner 

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ natty main 
# deb-src http://extras.ubuntu.com/ubuntu/ natty main 

deb http://security.ubuntu.com/ubuntu/ natty-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu/ natty-security main restricted 
deb http://security.ubuntu.com/ubuntu/ natty-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ natty-security universe 
deb http://security.ubuntu.com/ubuntu/ natty-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu/ natty-security multiverse 


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe 
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ maverick partner 
# deb-src http://archive.canonical.com/ubuntu/ maverick partner 

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ maverick main 
# deb-src http://extras.ubuntu.com/ubuntu/ maverick main 

deb http://security.ubuntu.com/ubuntu/ maverick-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu/ maverick-security main restricted 
deb http://security.ubuntu.com/ubuntu/ maverick-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ maverick-security universe 
deb http://security.ubuntu.com/ubuntu/ maverick-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu/ maverick-security multiverse 

```

---

### Post by koenn on 2010-11-29
> **Martiini said:**
> d
whoever says debian/ubuntu downgrade "is not possible and not supported" is a downright straight liar

you cannot do "apt-get dist-downgrade -t maverick" ... 
but .. 
you do 

/etc/apt/preferences
```
 ... 
```

/etc/apt/sources.list
```
 ... 
```


2 questions about this:

1- this procedure looks is incomplete ; merely editing those 2 files won't downgrade the system. I expect you need to invoke apt-get or dpkg or so in some way. What do you recommend ? 

2- from what I've seen in the past, calling apt-get upgrade or apt-get dist-upgrade with those configurations you suggest, will (more often that not) make dpkg exit with an error during the downgrade, leaving the entire system in an unknown, unstable state with some packages removed, some half-installed, and some not working because of broken dependencies. When that occurs, apt-get will not install or uninstall any packages until the original problem is fixed. This leaves the system unuseable.

Please explain how users who got in such a situation can get their systems up and running again.

---

### Post by Martiini on 2011-08-09
this thing doesnt apply anymore
ubuntu has disabled downgrading
debian is possible to downgrade

---

