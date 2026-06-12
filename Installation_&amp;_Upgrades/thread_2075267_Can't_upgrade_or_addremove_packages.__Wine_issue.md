---
title: "Can't upgrade or add/remove packages.  Wine issue?"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by bilmas on 2012-10-23
Hey everybody! I went to upgrade to 12.10 and it began downloading the packages but then the update manager disappeared.  I tried restarting it but it said that there were broken packages which could be repaired either in Synaptic or by using apt-get -f install.  I tried both things but still am having issues.  This is the output from Terminal:

> david@david:~$ sudo apt-get -f install
 Reading package lists... Done
 Building dependency tree 
 Reading state information... Done
 Correcting dependencies... Done
 The following packages were automatically installed and are no longer required:
 ttf-umefont fonts-horai-umefont libcapi20-3 unixodbc wine-gecko1.4
 winetricks webaccounts-extension-common libmpg123-0 libodbc1 ttf-droid
 libtiff5 libjbig0
 Use 'apt-get autoremove' to remove them.
 The following extra packages will be installed:
 libjbig0 libtiff5
 The following packages will be REMOVED:
 limbo wine wine1.3 wine1.4 wine1.4-amd64 wine1.4-common
 The following NEW packages will be installed:
 libjbig0 libtiff5
 0 upgraded, 2 newly installed, 6 to remove and 1977 not upgraded.
 15 not fully installed or removed.
 Need to get 0 B/196 kB of archives.
 After this operation, 114 MB disk space will be freed.
 Do you want to continue [Y/n]? y
 dpkg: error: parsing file '/var/lib/dpkg/status' near line 31989 package 'librtmp0:i386':
 blank line in value of field 'Original-Maintainer'
 E: Sub-process /usr/bin/dpkg returned an error code (2)

I have tried several things and it seems to me that the issue is that I have installed Wine1.3 and Wine1.4.  I am not sure when that happened as I don't even use Wine, but I have been unable to delete either by any command (purge, autoremove, etc).  There must be something I am missing and I was hoping somebody here knew what that thing was...

Thanks in advance!
David

---

### Post by dino99 on 2012-10-23
boot on recovery mode
then select root command 
and edit /etc/apt/sources.list with nano
comment out everything but the genuine ubuntu archives (main, universe, multiverse, restricted)
run again: clean/autoclean/autoremove and finally update
if it fail, then purge the cache:  sudo rm /var/apt/cache/archives/*
and update again
now you can exit to select "repair packages" from the previous menu

note: remember to use deborphan & bleachbit to clean the room from time to time.

---

### Post by bilmas on 2012-10-23
thanks for the advice! going to try that.

update: i went in to do that and it didn't seem like i had anything that wasn't genuine.  the header did say i was using oneric and the packages quantal.  that is weird since i am using precise.  here is the file.  maybe i am just missing something?

> # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to precise

thanks again for your help!

---

### Post by bilmas on 2012-10-24
still at a roadblock.  maybe somebody new will see this and know how to help?

thanks so much!
david

---

### Post by bilmas on 2012-10-26
reaching out again to see if this is familiar to anybody

thanks so much!

---

