---
title: "dependency problem while installing fatrat"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2011-09-29
Hi,
I am trying to install fatrat (download manager) and I am getting following dependency problems.
```

fatrat: Depends: libboost-date-time1.42.0 (>= 1.42.0-1) but 1.42.0-4ubuntu2 is to be installed
        Depends: libboost-system1.42.0 (>= 1.42.0-1) but 1.42.0-4ubuntu2 is to be installed
        Depends: libc6 (>= 2.4) but 2.13-0ubuntu13 is to be installed
        Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.21.3-1ubuntu1 is to be installed
        Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
        Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqt4-help (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
        Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
        Depends: libqt4-script (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
        Depends: libqt4-svg (>= 4:4.5.3) but 4:4.7.2-0ubuntu6 is to be installed
        Depends: libqt4-xml (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
        Depends: libqtwebkit4 (>= 2.0.0) but 2.1~really2.0.2-0ubuntu1 is to be installed
        Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
        Depends: fatrat-data (= 1.1.3-1ubuntu1) but 1.1.3-1ubuntu1 is to be installed

```

What next should I do to resolve this?
I am using Ubuntu 11.04  64 bit.

---

### Post by dino99 on 2011-09-29
that is called "partial" update, dont do it.
are you using third party repos (ppa/manual download) ?

---

### Post by tapas_mishra on 2011-09-29
But then how do I install it? I opened  Ubuntu Software Centre and typed fatrat and got the errors which I copy pasted above.
Here is my sources.list

```


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's

## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe

```
and in a folder /etc/apt/sources.list.d/
I have a file google-chrome.list which has 
```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

```

---

