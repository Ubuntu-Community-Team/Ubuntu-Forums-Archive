---
title: "Ubuntu Linux 10.04.3 - apt- Unable to find expected entry  all/binary-amd64/Packages"
date: 2017-08-01
forum: Installation &amp; Upgrades
---

### Post by garmanarnar on 2017-08-01
Hello Forums,

this is my first post and i hope it is in the right section.

I have trouble updating or upgrading my EOL Ubuntu 10.04.3 Server to a newer Version. 

I am picking up the slack of somebody else so please don't judge me for running an old EOL Version :oops:

So for now my plan was to edit the sources.list file and run: 

apt-get update
apt-get upgrade
apt-get dist-update


Unfortunately I have been trying to find a solution fpr days regarding the the following error "apt-get update" results in: 

```
USER:~$ sudo apt-get updateHit http://old-releases.ubuntu.com lucid Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid/all Translation-en_US
Hit http://old-releases.ubuntu.com lucid-updates Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid-backports Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://old-releases.ubuntu.com lucid-security Release.gpg
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://archive.canonical.com lucid Release
Ign http://old-releases.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://old-releases.ubuntu.com lucid Release
Hit http://old-releases.ubuntu.com lucid-updates Release
Hit http://old-releases.ubuntu.com lucid-backports Release
Hit http://old-releases.ubuntu.com lucid-security Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://old-releases.ubuntu.com lucid/main Packages
Hit http://old-releases.ubuntu.com lucid/restricted Packages
Hit http://old-releases.ubuntu.com lucid/main Sources
Hit http://old-releases.ubuntu.com lucid/restricted Sources
Hit http://old-releases.ubuntu.com lucid/universe Packages
Hit http://old-releases.ubuntu.com lucid/universe Sources
Hit http://old-releases.ubuntu.com lucid/multiverse Packages
Hit http://old-releases.ubuntu.com lucid/multiverse Sources
Hit http://old-releases.ubuntu.com lucid-updates/main Packages
Hit http://old-releases.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.canonical.com lucid/partner Sources
Hit http://old-releases.ubuntu.com lucid-updates/main Sources
Hit http://old-releases.ubuntu.com lucid-updates/restricted Sources
Hit http://old-releases.ubuntu.com lucid-updates/universe Packages
Hit http://old-releases.ubuntu.com lucid-updates/universe Sources
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-updates/multiverse Sources
Hit http://old-releases.ubuntu.com lucid-backports/main Packages
Hit http://old-releases.ubuntu.com lucid-backports/restricted Packages
Hit http://old-releases.ubuntu.com lucid-backports/universe Packages
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-backports/main Sources
Hit http://old-releases.ubuntu.com lucid-backports/restricted Sources
Hit http://old-releases.ubuntu.com lucid-backports/universe Sources
Hit http://old-releases.ubuntu.com lucid-backports/multiverse Sources
Hit http://old-releases.ubuntu.com lucid-security/main Packages
Hit http://old-releases.ubuntu.com lucid-security/restricted Packages
Hit http://old-releases.ubuntu.com lucid-security/main Sources
Hit http://old-releases.ubuntu.com lucid-security/restricted Sources
Hit http://old-releases.ubuntu.com lucid-security/universe Packages
Hit http://old-releases.ubuntu.com lucid-security/universe Sources
Hit http://old-releases.ubuntu.com lucid-security/multiverse Packages
Hit http://old-releases.ubuntu.com lucid-security/multiverse Sources
**W: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  all/binary-amd64/Packages in Meta-index file (malformed Release file?)**


**E: Some index files failed to download, they have been ignored, or old ones used instead.**



```

Here is my sources.plist:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to# newer versions of the distribution.


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid universe
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid multiverse
deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ lucid-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://old-releases.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse


## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner


deb http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu lucid-security main restricted
deb http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb-src http://old-releases.ubuntu.com/ubuntu lucid-security universe
deb http://old-releases.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu lucid-security multiverse



```

I dont have lots of experience regarding linux, especialy regarding repositories. 

I hope that someone can give me the right hint. It would be a great help
since I don't have the option to do a clean install.

Either this works or I have to migrate to an up-to-date OS / machine which will cost me a lot
of time and money..

---

### Post by wildmanne39 on 2017-08-01
With all the changes that have been made since 10.04 reached EOL it is best to back up all important data and install a fresh new server version. There was a lot of changes from 10.04 to 12.04 and upgrades failed often at that time, now Ubuntu uses systemd as well, it is just my opinion but I do not think upgrading is the way to go and it will take a lot longer to upgrade then to install a fresh new server version in either case back up important data first.

---

### Post by Bucky Ball on 2017-08-01
+1 to all of the above. Too far gone. ;)

---

