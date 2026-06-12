---
title: "What is best way to dist-upgrade with a debmirror"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by bagpussnz on 2008-07-09
Hi,
I have a debmirror for feisty, gutsy and hardy (on a server called ubuntuupdate).
I have a number of users on feisty and I want to upgrade them to hardy. What is the best way to do the upgrade?

(apt-get dist-upgrade doesn't see any upgrade - do I just have to change feisty to hardy in the sources.list??)

My sources.list is....

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty main restricted
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-updates main restricted
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty universe
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty multiverse
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-backports main restricted universe multiverse
# deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-backports main restricted universe multiverse

deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security main restricted
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security main restricted
deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security universe
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security universe
deb [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security multiverse
deb-src [http://ubuntuupdate/feisty](http://ubuntuupdate/feisty) feisty-security multiverse

Cheers,
Ian.

---

