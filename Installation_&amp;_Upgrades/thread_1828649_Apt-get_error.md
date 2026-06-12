---
title: "Apt-get error"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by vladutz on 2011-08-19
Hello

Im a first time user of Ubuntu, I have 11.04 64bit installed. I used to use Fedora before.

Seems like all of a sudden APT-GET stopped working. Whatever I try to install, it either tells me dependencies unmet presumably because the libraries are uninstalable (as it it says), and then when I try to install these packages I always get the error "E:Package xxxx has no installation candidate". This is for anything I try. I use Main server in Software Source, but have tried different servers too.
Any idea how to fix this? 
Im posting the result of  cat /etc/apt/sources.list

May I point out that I haven't touched it, one day it was working the next it was not. Very Windows-like

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes)  for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty  restricted

## Major bug fix updates produced after the final  release of the
## distribution.
deb  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted
deb-src  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted

## N.B.  software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##  team. Also, please note that software in universe WILL NOT receive any
##  review or updates from the Ubuntu security team.
deb  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty  universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B.  software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
##  team, and may not be under a free licence. Please satisfy yourself as  to 
## your rights to use the software. Also, please note that  software in 
## multiverse WILL NOT receive any review or updates  from the Ubuntu
## security team.
deb  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

##  Uncomment the following two lines to add software from the 'backports'
##  repository.
## N.B. software from this repository may not have been  tested as
## extensively  as that contained in the main release, although it includes
## newer  versions of some applications which may provide useful features.
##  Also, please note that software in backports WILL NOT receive any review
##  or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/)  natty-backports main restricted universe multiverse
# deb-src  [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-backports main restricted  universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)  natty-security multiverse

## Uncomment the following two lines to  add software from Canonical's
## 'partner'  repository.
## This software is not part of Ubuntu, but is offered  by Canonical and the
## respective vendors as a service to Ubuntu  users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty  partner

## This software is not part of Ubuntu, but is offered by  third-party
## developers who want to ship their latest software.
deb  [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)  natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by dino99 on 2011-08-19
makes some cleaning first:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a
( can be long, dont stop it before ending)

sudo apt-get update
sudo apt-get install -f

have you tried synaptic/update-manager/aptitude for comparison ?

note: if you dont compile yourself, then deb-scr lines can be commented

---

### Post by vladutz on 2011-08-21
Hello
Sorry about the delay in replying, thanks for your advice
I did what you said, but I still can't seem to install (mostly) anything. I was able to apt-get install ubuntu-restricted-extras, but thast just about it.
I'm trying to install apt-file, and it says:
apt-file : Depends: curl but it is not installable
            Depends: liblist-moreutils-perl but it is not installable
E: Broken packages


So I try to install each of them:
sudo apt-get install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package curl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'curl' has no installation candidate

Could it be it has a different name? That's why I was trying to install apt-file for.

So then I try to install Stellarium:
sudo apt-get install stellarium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 stellarium : Depends: libqt4-network (>= 4:4.6.0) but it is not installable
              Depends: libqt4-opengl (>= 4:4.6.1) but it is not installable
              Depends: libqt4-script (>= 4:4.6.0) but it is not installable
              Depends: libqt4-sql (>= 4:4.6.0) but it is not installable
              Depends: libqt4-sql-sqlite but it is not installable
E: Broken packages


I try to install each of them packages but of course it fails - otherwise it would have done it by itself.

I don't understand why it's doing this, I only installed it a week ago and everything worked fine for the first 3 days.

---

