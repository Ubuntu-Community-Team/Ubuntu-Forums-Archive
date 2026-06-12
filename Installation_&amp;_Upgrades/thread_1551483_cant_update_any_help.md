---
title: "cant update any help"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by barah on 2010-08-12
cant update give me this error 
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
 

and when i press in details i have this 
libgirepository1.0-1

---

### Post by tommcd on 2010-08-12
> **barah said:**
> cant update give me this error 
Package dependencies cannot be resolved

You need to provide some more info here.
Please answer all of these questions:
1. What version of Ubuntu are you running?

2. Is this a wubi (inside Windows) install? Or is this a real install to a dedicated linux partition?

3. Was this a new install? Or an upgrade from a previous Ubuntu version?

4. Open a terminal (applications > accessories > terminal) and try to update the system with apt-get:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If you get errors, post them here.

5.Post here your */etc/apt/sources.list* file.

6. ##Most important## Are you trying to install **gnome shell**? Are you using a ppa repo for this? If so, see this:
[http://ubuntuforums.org/showthread.php?p=9711618](http://ubuntuforums.org/showthread.php?p=9711618)
Googling *libgirepository1.0-1 +ubuntu* returns a bunch of links about gnome shell.

And welcome to the Ubuntu forums!

---

### Post by barah on 2010-08-12
1- its version 10.04
2- its alone without windwos
3- i try to make update to it ;)
4- i try bye terminal and give me many error 
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://jo.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jo.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://jo.archive.ubuntu.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://jo.archive.ubuntu.com/ubuntu/ maverick universe
deb http://jo.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://jo.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://jo.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://jo.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://jo.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
# deb http://thebachman.info/debian/mercury-unstable ./ # disabled on upgrade to maverick
deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
deb http://jo.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb-src http://jo.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://jo.archive.ubuntu.com/ubuntu/ maverick-backports restricted main multiverse universe
deb-src http://jo.archive.ubuntu.com/ubuntu/ maverick-backports restricted main multiverse universe


```
source file contant 
any help much thx ;)

---

### Post by mörgæs on 2010-08-13
It seems like you are on your way to upgrade to Ubuntu 10.10, is this intended?

---

### Post by tommcd on 2010-08-13
> **barah said:**
> 1- its version 10.04
3- i try to make update to it ;)
4- i try bye terminal and give me many error 
-------------------
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) maverick main restricted
....

You say you are running 10.04, but the commented out cdrom indicates Jaunty 9.04. *And* the repos you are trying to update from say **Maverick**, which is Ubuntu 10.10. 
You also have some commented out Jaunty repos in your output.
```
# deb http://jo.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```

And to screw things up even more, you also have some ppa repos from Karmic 9.10 thrown in there!!!
```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
```
Also, you got some stuff I never even heard of before like the commented out:
```
 deb http://thebachman.info/debian/mercury-unstable
```
*This is why you are having problems updating. You should only be updating from ONE repo*. 

If you are running Jaunty 9.04, you need to point all the repos in your /etc/apt/sources.list to Jaunty. If you are indeed running Lucid 10.04, then you need to point your sources.list to lucid. And comment out those 3rd party repos until you get this sorted out.
You have made a mess of your system. Stick with the *standard default* Ubuntu repos from now on and you will not have these problems.

Can you post here your: */etc/apt/sources.list* file????

---

