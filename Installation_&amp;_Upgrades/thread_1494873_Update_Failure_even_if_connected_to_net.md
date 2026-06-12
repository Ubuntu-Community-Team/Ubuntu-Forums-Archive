---
title: "Update Failure even if connected to net"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by apurvaagarwal87 on 2010-05-27
I upgraded to Ubuntu 10.04 (Lucid Lynx). I am able to surf the net, but am not able to update the packages using Update Manager. I faced this problem when I was on Karmic too and had hoped that upgrading to Lucid would solve it.

Error Message

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid/Release.gpg](http://ubuntu.qualitynet.net/ubuntu/dists/lucid/Release.gpg)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/Release.gpg](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/Release.gpg)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/Release.gpg](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/Release.gpg)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2](http://ubuntu.qualitynet.net/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_IN.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_IN.bz2)  
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/Release.gpg)  
Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.


I am also posting /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid main restricted
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates main restricted
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid universe
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid universe
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates universe
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid multiverse
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid multiverse
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates multiverse
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security main restricted
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security main restricted
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security universe
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security universe
deb [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security multiverse
deb-src [http://ubuntu.qualitynet.net/ubuntu/](http://ubuntu.qualitynet.net/ubuntu/) lucid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid

##Themes du project bisigi

---

