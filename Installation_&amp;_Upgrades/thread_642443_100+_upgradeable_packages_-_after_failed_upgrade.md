---
title: "100+ upgradeable packages - after failed upgrade"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by chrisruls00 on 2007-12-16
After failing to upgrade to 7.10 Kubuntu it says I have 1000+ packages to upgrade! I tried to upgrade them but It just keeps giving me errors! Can anyone help me? Also various KDE application tend to crash a lot.

---

### Post by bapoumba on 2007-12-16
Please give your source.list:
```
cat /etc/apt/sources.list
```
and the errors to:
```
sudo aptitude update
```

---

### Post by chrisruls00 on 2007-12-16
Sources

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
# deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

errors:

It dosent give me any when I run from the terminal

I noticed that it is getting things from the gusty servers even though my computer still says its 7.04, is this my problem?

Also! I'm not sure if its important, but I started with regular Ubuntu and switched to Kubuntu.

---

### Post by bapoumba on 2007-12-17
You have gutsy repos in your sources.list.
You said your upgrade did not work properly. In order to finish it, please run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you are using kubuntu, please make sure you have kubuntu-desktop installed.

---

