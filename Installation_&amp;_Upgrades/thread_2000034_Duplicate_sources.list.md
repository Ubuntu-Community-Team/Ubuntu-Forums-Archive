---
title: "Duplicate sources.list"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by namaster on 2012-06-08
When I try to run sudo apt-get update I get below error. In order to resolve the issue, ubuntu tells me to run apt-get update again? 

Can someone please tell me how to fix the issue manually?

```
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                 
Fetched 22.0 MB in 1min 26s (256 kB/s)                                                                                                   
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ oneiric/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Here is my source list:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

# Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse
deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric universe multiverse

## Medibuntu - Ubuntu 8.04 "hardy" 
## Please report any bug on https://bugs.launchpad.net/medibuntu/ 
# deb http://packages.medibuntu.org/ lucid free non-free # disabled on upgrade to lucid

# deb http://ppa.launchpad.net/compiz/ubuntu lucid main # disabled on upgrade to lucid
deb http://extras.ubuntu.com/ubuntu oneiric main #Third party developers repository


```

---

### Post by diesch on 2012-06-08
What does
```
egrep 'universe|multiverse' /etc/apt/sources.list /etc/apt/sources.list.d/*
```
print?

---

### Post by namaster on 2012-06-09
```
hell@hell-laptop:~$ egrep 'universe|multiverse' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:## universe WILL NOT receive any review or updates from the Ubuntu security
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
/etc/apt/sources.list:# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
/etc/apt/sources.list:# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu oneiric-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse
/etc/apt/sources.list:deb-src http://archive.ubuntu.com/ubuntu oneiric universe multiverse

```

---

### Post by diesch on 2012-06-09
Remove the lines
```

deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse 
deb http://archive.ubuntu.com/ubuntu oneiric universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu oneiric universe multiverse 

```from [I]/etc/apt/sources.list

[/I]They are above the line
```
## Medibuntu - Ubuntu 8.04 "hardy" 
```

---

