---
title: "Gutsy still not in Update Manager"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by taz5005 on 2008-01-21
I've been trying to upgrade to Gutsy for a while now (obviously not that urgently) but my update manager can't find it.  I've looked at all the previous posts about this topic and tried everything, but it just isn't working.  I've ran all of this :
```
sudo apt-get upgrade
sudo apt-get update
sudo update-manager --dist-ugprade
sudo update manager -c -d

```
to no avail.

I've checked out [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) and done everything it said, including making sure this file : /var/lib/update-manager/meta-release has everything in it that it needs.

I don't know what else to do...here's my sources list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
# deb http://www.getautomatix.com/apt feisty main
# deb http://www.getautomatix.com/apt feisty main
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
# deb http://www.getautomatix.com/apt feisty main
```

Any help would be great!:confused::confused:

---

### Post by Partyboi2 on 2008-01-21
```
sudo update-manager --check-dist-upgrades
```
You could try the alternate cd to upgrade

---

