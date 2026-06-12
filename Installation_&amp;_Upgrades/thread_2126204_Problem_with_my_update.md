---
title: "Problem with my update"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by long2511mdd on 2013-03-16
I am trying to update my ubuntu but I do not know why I receive this mass:

"W: Failed to fetch [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal/Release.gpg](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal/Release.gpg)  Something wicked happened resolving 'az-1.hpcloud.mirror.websitedevops.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-updates/Release.gpg](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-updates/Release.gpg)  Something wicked happened resolving 'az-1.hpcloud.mirror.websitedevops.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-backports/Release.gpg](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-backports/Release.gpg)  Something wicked happened resolving 'az-1.hpcloud.mirror.websitedevops.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-security/Release.gpg](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/dists/quantal-security/Release.gpg)  Something wicked happened resolving 'az-1.hpcloud.mirror.websitedevops.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
"

This is my sources.list:
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal main restricted
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates main restricted
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal universe
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal universe
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates universe
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal multiverse
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal multiverse
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates multiverse
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security main restricted
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security main restricted
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security universe
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security universe
deb [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security multiverse
deb-src [http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/](http://az-1.hpcloud.mirror.websitedevops.com/ubuntu/) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.


What I should do now?? Please help

---

### Post by ibjsb4 on 2013-03-16
> HP has graciously donated 3 months of computing time  to Ubuntu Developers! This is a great contribution so we need to ensure  we use it to it's full potential.  
This  is a pilot/beta testing to give HP feedback on their Ubuntu powered  cloud, as well as give Ubuntu developers a chance to familiarize  themselves with the cloud, juju, and all the associated tools.  

[https://wiki.ubuntu.com/HPCloud](https://wiki.ubuntu.com/HPCloud)

Why are you on this?

---

### Post by long2511mdd on 2013-03-16
I go to "Software Resources" and find best server, that's what happened next after I update

---

### Post by ibjsb4 on 2013-03-16
Go back to software sources and choose the "main server" or choose one from you country either using software source list or this one:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

