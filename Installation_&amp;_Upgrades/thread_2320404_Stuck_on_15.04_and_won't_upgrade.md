---
title: "Stuck on 15.04 and won't upgrade"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by cocjh1 on 2016-04-13
Hi,

I'm running version 15.04 and unable to upgrade my distribution to 15.10.  I can't remember if I've had a failed upgrade in the past, but is there any way to force the upgrade to happen now please?  Below is the output from apt-get upgrade, which for so reason doesn't think there's an upgrade available.  Any help much appreciated:

```

chris@blade:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

```

chris@blade:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

Some outputs which may help:
```

chris@blade:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```

```

chris@blade:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb-src http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner

```

---

### Post by Bashing-om on 2016-04-13
cocjh1; Hello;

The tutorial :
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
To release upgrade from an END_Of_Life release.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

