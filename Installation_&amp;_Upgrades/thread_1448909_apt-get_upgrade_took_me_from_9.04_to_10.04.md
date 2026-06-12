---
title: "apt-get upgrade took me from 9.04 to 10.04"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by pingtoft on 2010-04-07
Apr. 5th I ran a 'apt-get upgrade' on my jaunty box.
I was a little surprised at how much apparently needed upgrading and even more surprised when after boot it said 10.04 lucid.

AFAIK 'upgrade' shouldn't upgrade the kernel so I'm a little confused :confused:

I recently added the following to my sources.list:
```
deb http://dk.archive.ubuntu.com/ubuntu lucid main universe
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main
```
Could this cause the kernel to be upgraded?

---

### Post by Megaptera on 2010-04-07
I think there's a difference between 'update' and 'upgrade' ... was it 'updates' you were looking to do?

---

### Post by philinux on 2010-04-07
> **pingtoft said:**
> Apr. 5th I ran a 'apt-get upgrade' on my jaunty box.
I was a little surprised at how much apparently needed upgrading and even more surprised when after boot it said 10.04 lucid.

AFAIK 'upgrade' shouldn't upgrade the kernel so I'm a little confused :confused:

I recently added the following to my sources.list:
```
deb http://dk.archive.ubuntu.com/ubuntu lucid main universe
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main
```
Could this cause the kernel to be upgraded?

The kernel lives in main so by adding the lucid repo you got the lucid kernel.
Lets have a look at your full sources list. 
Open a terminal.
```
cat /etc/apt/sources.list
```

---

### Post by philinux on 2010-04-07
> **Megaptera said:**
> I think there's a difference between 'update' and 'upgrade' ... was it 'updates' you were looking to do?

If you use update manager it basically performs this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by pingtoft on 2010-04-07
I had a feeling it had something to do with my changes to the sources.list - I just expected that I would have to do a 'dist-upgrade' to upgrade the kernel. 
Thanks for clearing it up for me :)

My sources.list as requested:
```
#
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
#deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
#deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu jaunty main
deb http://dk.archive.ubuntu.com/ubuntu lucid main universe
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu jaunty main

```

---

