---
title: "Precise - Update gives me error"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by ubunteshwar on 2012-10-22
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise/Release](http://archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/precise-security/Release](http://archive.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'commercial/source/Sources' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

lsb_release -a; echo; cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done

[http://paste.ubuntu.com/1298480/](http://paste.ubuntu.com/1298480/)

---

### Post by dino99 on 2012-10-22
comment out the canonical line into /etc/apt/sources.list

( or remove the typo)

if you does not know what to do, then post it here  ( cat /etc/apt/sources.list)

---

### Post by ubunteshwar on 2012-10-23
Thanks for the response. I am not sure what you asked me to do.  

$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ oneiric main restricted
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted commercial

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted commercial

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse commercial

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted commercial
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

---

### Post by plucky on 2012-10-24
Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove **commercial** from all the lines.

> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted commercial
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted commercial
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse commercial

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted commercial
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted commercial

Good Luck

---

### Post by ubunteshwar on 2012-10-24
> **plucky said:**
> Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove **commercial** from all the lines.


This solved my problem. Thanks plucky!

---

