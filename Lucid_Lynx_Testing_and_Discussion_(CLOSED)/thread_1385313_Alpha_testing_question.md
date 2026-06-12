---
title: "Alpha testing question"
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeremyjjbrown on 2010-01-19
Hi,

After about a year and a half of Ubuntu I finally feel ready to start running Alpha/Beta releases on one of my four Ubuntu machines so I can report bugs and make a small contribution to the cause. 

My question is if I install 10.04 Alpha 2, how does it update? I assume  Update Manager automatically prompts to install the packages for Beta 1, 2, RC, LTS at the appropriate times. I couldn't find a definitive answer with google.

Thanks

---

### Post by Uncle Spellbinder on 2010-01-19
There's a separate subforum for Alpha/Beta/Testing discussion. Might get a quicker answer there.

[Lucid Lynx Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by garvinrick4 on 2010-01-19
You will have Lucid Lynx repositories that will fetch your updates && upgrades just like any other version of Ubuntu. If you do daily upgrades just stay say no to partial upgrades. Expect
some weird things to happen but that is part of testing. Enjoy

---

### Post by mcduck on 2010-01-19
> **jeremyjjbrown said:**
> Hi,

After about a year and a half of Ubuntu I finally feel ready to start running Alpha/Beta releases on one of my four Ubuntu machines so I can report bugs and make a small contribution to the cause. 

My question is if I install 10.04 Alpha 2, how does it update? I assume  Update Manager automatically prompts to install the packages for Beta 1, 2, RC, LTS at the appropriate times. I couldn't find a definitive answer with google.

Thanks

During the development the packages are update as soon as the developers get them ready, and when running the development version there will be no actual steps (like beta1, beta2, RC etc). The updates are just a smooth progression, you start with what you install, get a update for couple packages every now and then, and at some point you'll be running the final release.

The only thing you sould note (apart from the generic idea of development releases being at leeast a bit unstable) is that since the packages are really added when they are ready, things might be a bit broken every now and then. For example when some package has already been updated while some other package it depends on is still old version. In those cases just wait for some hours/days and things will usually work again correctly. And also you'd better use Synaptic (or apt-get dist-upgrade) for updating instead of the Update Manager (or apt-get upgrade). Dist-upgrade (and Synaptic) are able to uninstall packages that aren't required any more, which is something that can happen during the development. And of course always check what packages are updating and if there are any that can't for some reason be updated..

---

### Post by bodhi.zazen on 2010-01-19
> **Uncle Spellbinder said:**
> There's a separate subforum for Alpha/Beta/Testing discussion. Might get a quicker answer there.

[Lucid Lynx Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=377)

Indeed ...

---

### Post by Kevbert on 2010-01-19
The way I usually update is via terminal with
```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by jeremyjjbrown on 2010-01-19
> **Kevbert said:**
> The way I usually update is via terminal with
```
sudo aptitude update
sudo aptitude safe-upgrade
```

Thanks Everyone!

I like your method Kevbert. I'm not advanced yet, and I've had batshit crazy things start happening when I use "apt-get dist-upgrade". Such as dozens of really important packages purging themselves all at once. When I get the occasional isolated error I get to learn how to fix Ubuntu.:) When big problems happen I get practice rebuilding my system.:(

---

### Post by VMC on 2010-01-19
> **Kevbert said:**
> The way I usually update is via terminal with
```
sudo aptitude update
sudo aptitude safe-upgrade
```

I do the same thing, except I have it on a file(xx) with this inside:
```
sudo aptitude update && sudo aptitude safe-upgrade

```
So from a terminal I just type "./xx" then sudo password and away it goes, waiting for my yea or nay at the end.

---

### Post by jeremyjjbrown on 2010-01-20
Alpha 2 is installed an running great.

This new Distro feels really impressive.

Is there a Multiverse Repo for Lucid? Had no luck enabling that source.

---

### Post by cookiecruncher on 2010-01-20
> **jeremyjjbrown said:**
> Is there a Multiverse Repo for Lucid? Had no luck enabling that source.

Mine seems to be enabled by default.

```
cat /etc/apt/sources.list                
#deb cdrom:[Kubuntu 10.04 _Lucid Lynx_ - Alpha i386 (20100112.3)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://za.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse


```

I'm in South Africa, thus the 'za'.

---

### Post by jeremyjjbrown on 2010-01-20
Hmmm, I'll check my sources list better. I should have looked closely when I enabled backports.

---

