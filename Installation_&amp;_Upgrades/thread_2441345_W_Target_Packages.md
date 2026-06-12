---
title: "W: Target Packages"
date: 2020-04-22
forum: Installation &amp; Upgrades
---

### Post by moafaneh on 2020-04-22
Hello i have this problem when i enter 
```
sudo apt update
```

and i get this 

```
Hit:1 http://archive.ubuntu.com/ubuntu eoan InRelease               
Hit:2 http://security.ubuntu.com/ubuntu eoan-security InRelease     
Hit:3 http://jo.archive.ubuntu.com/ubuntu eoan InRelease
Hit:4 http://archive.ubuntu.com/ubuntu eoan-updates InRelease
Hit:5 http://jo.archive.ubuntu.com/ubuntu eoan-updates InRelease
Hit:6 http://jo.archive.ubuntu.com/ubuntu eoan-backports InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:46 and /etc/apt/sources.list:59
```


so I entered this code to check what is wrong 

```
cat /etc/apt/sources.list
```

 
then i get this respond 

```
# deb cdrom:[Ubuntu 19.04 _Disco Dingo_ - Release amd64 (20190416)]/ disco main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ eoan main restricted
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ eoan-updates main restricted
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ eoan universe
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco universe
deb http://jo.archive.ubuntu.com/ubuntu/ eoan-updates universe
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jo.archive.ubuntu.com/ubuntu/ eoan multiverse
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco multiverse
deb http://jo.archive.ubuntu.com/ubuntu/ eoan-updates multiverse
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ eoan-backports main restricted universe multiverse
# deb-src http://jo.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu disco partner
# deb-src http://archive.canonical.com/ubuntu disco partner

deb http://security.ubuntu.com/ubuntu eoan-security main restricted
# deb-src http://security.ubuntu.com/ubuntu disco-security main restricted
deb http://security.ubuntu.com/ubuntu eoan-security universe
# deb-src http://security.ubuntu.com/ubuntu disco-security universe
deb http://security.ubuntu.com/ubuntu eoan-security multiverse
# deb-src http://security.ubuntu.com/ubuntu disco-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
deb http://archive.ubuntu.com/ubuntu eoan main restricted # auto generated by ubuntu-release-upgrader
deb http://archive.ubuntu.com/ubuntu eoan-updates main restricted # auto generated by ubuntu-release-upgrader
deb http://security.ubuntu.com/ubuntu eoan-security main restricted # auto generated by ubuntu-release-upgrader
# see the sources.list(5) manual.
```

please help me

---

### Post by lvm on 2020-04-22
It is trying to tell you in rather too many words that lines 46 and 59 are identical and one of them has to be deleted or commented out.

---

### Post by moafaneh on 2020-04-22
Thank you so much 
problem solved

---

