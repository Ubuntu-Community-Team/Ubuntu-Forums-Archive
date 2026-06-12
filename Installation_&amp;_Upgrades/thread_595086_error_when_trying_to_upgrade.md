---
title: "error when trying to upgrade"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by yowshi on 2007-10-28
i got these errors when i tried to upgrade from fiesty to gusty using the update manager




Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/Release.gpg](http://www.getautomatix.com/apt/dists/feisty/Release.gpg) Could not resolve 'www.getautomatix.com'
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-en_CA.bz2](http://www.getautomatix.com/apt/dists/feisty/main/i18n/Translation-en_CA.bz2) Could not resolve 'www.getautomatix.com'
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz) Could not resolve 'www.getautomatix.com'

---

### Post by Pumalite on 2007-10-28
Before upgrading you have to totally remove automatix.

---

### Post by yowshi on 2007-10-28
i have uninstalled it but it still wont upgrade

Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)

is what i get

---

### Post by Pumalite on 2007-10-28
You have to also uninstall all programs that you have installed through third parties.

---

### Post by yowshi on 2007-10-28
i dont remember which programmes would have been installed with that one

---

### Post by avik on 2007-10-28
I don't think you have to do anything that drastic.  Can you post your /etc/apt/sources.list please?

---

### Post by yowshi on 2007-10-28
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main

#AUTOMATIX REPOS START


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by Pumalite on 2007-10-28
To start with you should comment out (#) your Automatix repos

---

### Post by yowshi on 2007-10-28
ok so i commented out both that automatix and the dfeer stuff this is gonna take all night to finish though the download is so slow and the speed not stable

---

### Post by Pumalite on 2007-10-28
[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by yowshi on 2007-10-28
i would rather upgrade then clean install mainly because there is no easy way to back up like 100+ gigs of data

---

### Post by avik on 2007-10-28
Backups are always a good idea, but if you must upgrade, just wait for the servers.  Nothing else to do.

---

### Post by yowshi on 2007-10-28
i've never had a pressing need for backing up of already saved files. in my entire life i have lost like 3 hard disks if that

thing is in the past when i have had to it wasnt as big a deal as it is now. since i have never downloaded installed or saved as much on one computer as i now have

---

