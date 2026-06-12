---
title: "install x11vnc in 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by alfonso78 on 2011-10-15
Hi,

I'm trying to have x11vnc installed in my bootable usb stick with 11.10.

```
ubuntu@ubuntu:~$ sudo apt-get update
*[...]*
ubuntu@ubuntu:~$ sudo apt-get install x11vnc
Reading package lists... Done
Building dependency tree
Reading state information... Done
**E: Unable to locate package x11vnc**
```

In order to be able to install the package, you have to edit **/etc/apt/sources.list**:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo vi /etc/apt/sources.list
```

I used the sources.list found at [http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3) :

```
#
# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted

#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/main/binary-i386/
#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ dists/oneiric/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 11.10 _Oneiric Ocelot_ - Release amd64 (20111011)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://de.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://de.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main


```

Now try again:

```
ubuntu@ubuntu:~$ sudo apt-get install x11vnc
```

and this time it works! :)

---

