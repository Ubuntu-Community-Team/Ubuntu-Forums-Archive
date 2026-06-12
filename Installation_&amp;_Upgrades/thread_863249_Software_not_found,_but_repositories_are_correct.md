---
title: "Software not found, but repositories are correct"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Teufel on 2008-07-18
Hello,

I'm trying to install Adobe Reader Plugin for Firefox.

This is my shell output:

```
dom@laptop:~$ sudo apt-get install mozilla-acroread
[sudo] password for dom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-acroread

```

Well, this is my sources.list:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu hardy-security universe

```

I'm pretty positive Multiverse is availabe, I also checked it manually in Administration -> Software Sources.

Any ideas?

Thanks.

---

### Post by NilsE on 2008-07-18
Have you searched in Synaptic to verify the name?  I am not sure that is a valid package name for the Adobe reader plugin.

---

### Post by Teufel on 2008-07-18
Synaptic does not find anything either and I'm positive about the name, I had it installed before.

---

### Post by avtolle on 2008-07-18
Someone correct me if I'm wrong, but isn't Adobe Reader obtained from the Medibuntu repositories?

---

### Post by NilsE on 2008-07-18
> **avtolle said:**
> Someone correct me if I'm wrong, but isn't Adobe Reader obtained from the Medibuntu repositories?
You are 100% correct.  Just checked

---

### Post by avtolle on 2008-07-18
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to install the Medibuntu repositories. Run the commands given in the wiki article, and then try to install.

---

