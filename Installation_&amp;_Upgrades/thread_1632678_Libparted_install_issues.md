---
title: "Libparted install issues"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by doctorzeus on 2010-11-28
Hi all,

I am trying to install gparted from synaptic package manager however I get the error:

> 
Could not mark packages for installation or upgrade

gparted:
 Depends: libparted0 but it is not going to be installed


So I tried installing it manually using apt-get:

> sudo apt-get install libparted0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libparted0: Depends: libparted0debian1 (= 2.2-5ubuntu5) but 2.2-5ubuntu5.1 is to be installed
E: Broken packages

Obliviously the problem is with libparted0, can anyone help me on this one please?

---

### Post by dino99 on 2010-11-28
if you mix release or distro or use ppa, you get such issue: check synaptic repo tab or /etc/apt/sources.list

---

### Post by kansasnoob on 2010-11-28
You might try going to synaptic and clicking on Edit > fix broken packages.

---

### Post by doctorzeus on 2010-11-28
> **dino99 said:**
> if you mix release or distro or use ppa, you get such issue: check synaptic repo tab or /etc/apt/sources.list

Output of Sources.list:
```

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe
```

Haven't installed anything that should conflict with it to my knowledge, biggest thing I've done is downgrade GDM...

---

