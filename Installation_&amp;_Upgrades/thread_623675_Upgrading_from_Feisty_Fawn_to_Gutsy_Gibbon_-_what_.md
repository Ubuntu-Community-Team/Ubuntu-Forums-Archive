---
title: "Upgrading from Feisty Fawn to Gutsy Gibbon - what to update in Feisty fisrst ?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by bewire on 2007-11-26
Hi, I'm planning to upgrade my Feisty Fawn system, and I have some questions related to the preparations, ref the doc pages:

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

[I]Before you start
You can only directly upgrade to Ubuntu 7.10 ("Gutsy Gibbon") from Ubuntu 7.04 ("Feisty Fawn") (see UpgradeNotes). 

**Be sure that you have all updates applied to Ubuntu 7.04 before you upgrade. **

Before upgrading it is recommended that you read the  release notes for Ubuntu 7.10, which document caveats and workarounds for known issues in this version. [/I]

**Preparations**
Question: How do I check if I have alle updates ? Normally I have been using apt-get to manage packages, but I'm not sure how to check and make a full update of the system. 

**Upgrading**
I just installed the update-manager-core as described at the same page:

[I]If you run an Ubuntu server, you should use the new server upgrade system. 

Install update-manager-core if it is not already installed: 

sudo aptitude install update-manager-core
Launch the upgrade tool: 

sudo do-release-upgrade
Follow the on-screen instructions. [/I]
Question:
- Should I wait to install this package until the system is updated ?
-What lines should be be in the sources.list ? Below is my existing sources.list:

```
#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://no.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://bazaar-vcs.org/releases/debs/feisty ./

```

---

