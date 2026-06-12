---
title: "E: Unable to locate package cvs"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by sajerg281 on 2014-10-20
I want to install cvs using the command sudo apt-get install cvs but gives the error "E: Unable to locate package cvs".

The output of the command cat /etc/apt/sources.list is 

#deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64+mac (20121017.3)]/ quantal main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal main restricted
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal main restricted
## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal universe
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal universe
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates universe
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal multiverse
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

the output of the command sudo apt-get update is

Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg     
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en
Reading package lists... Done

how can I solve the problem?
thanks,

---

### Post by nerdtron on 2014-10-20
Ubuntu 12.10 has reached end-of-life and is no longer supported. It is not a Long-Term-Support release.
See more: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You should probably upgrade to a newer version, 14.04 and 12.04 are LTS releases.

---

