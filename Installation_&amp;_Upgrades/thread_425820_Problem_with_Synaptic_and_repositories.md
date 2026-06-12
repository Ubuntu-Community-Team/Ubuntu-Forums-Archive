---
title: "Problem with Synaptic and repositories"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by whein on 2007-04-27
I've been having problems both in Edgy and Fiesty getting Synaptic to see all the packages available.  As far as I can tell I have all the right repositories enabled, but certain packages I _know_ should be available aren't.  For instance, I went to go install ivtv-utils tonight.  Not only do I know it's in the [ubuntu repositories]("http://packages.ubuntu.com/feisty/x11/ivtv-utils") but I already downloaded it locally and stuck it in a personal repository set up on my computer using [this guide]("https://help.ubuntu.com/community/PersonalRepositories").  Yet Synaptic has no clue it exists.  And yes, I ran the script to refresh Packages.gz as well as running both apt-get update and hitting the reload button in Synaptic a half dozen times.  Yes, the local repo is called out correctly in my sources.list as shown below.  But for whatever reason, the only way I could get it to install was to right click on the file from Nautilus and use the GDebi Package Installer.  Now I'm running into the same problem with mplayer not finding some of the files it depends on to install:
```
mplayer:
 Depends: libfaac0 (>=1.24clean) but it is not installable
 Depends: liblame0 (>=3.96.1) but it is not installable
 Depends: libmp4v2-0 (>=2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
 Depends: libxvidcore4 (>=1:1.0.0-0.0) but it is not installable
 Depends: mplayer-skins  but it is not installable
```

This is my sources.list:
```
deb file:/usr/local/FiestyRepository ./

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

Any takers? :(
-Will

---

### Post by zvacet on 2007-04-28
> ## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main




I hope this will help you.

---

