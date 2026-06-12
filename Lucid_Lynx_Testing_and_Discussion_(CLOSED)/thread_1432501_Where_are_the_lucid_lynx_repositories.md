---
title: "Where are the lucid lynx repositories?"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by d3v1150m471c on 2010-03-17
Where can I get a list of the lucid lynx repositories?

---

### Post by k3lt01 on 2010-03-18
What do you mean by list? Do you mean a list of programs? If you want a list of programs go [here]("http://packages.ubuntu.com/"). Scroll down and click on Lucid.

The repositories themselves are [here]("http://archive.ubuntu.com/ubuntu/"). Click on the dists link and scroll down the bottom of the page and you will see Lucid.

---

### Post by d3v1150m471c on 2010-03-18
Thanks mate. I am looking for the source link to add to my software sources. Namely the security updates.

---

### Post by Chame_Wizard on 2010-03-18
Just enable all repositories+add the back-ports.

---

### Post by meborc on 2010-03-18
the old school way was to just take your karmic source.list and change all karmic to lucid ;)

---

### Post by ankspo71 on 2010-03-18
Hi,
I have not actually used this link myself, but I had it bookmarked in case I messed up my repos or something lol. 
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
it is a web based ubuntu source list generator.
It also has 3rd party repos etc. (after you select your country and Ubuntu version)
Hope it works.

---

### Post by k3lt01 on 2010-03-18
meborc has it spot on.

```
# 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic universe
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main
deb http://packages.sil.org/ubuntu karmic main
deb http://www.geekconnection.org/remastersys/repository karmic/
```

This is my sources.lists on my Karmic install, if I was to update this to Lucid I would simply change every reference from karmic to lucid. Then I would update and upgrade. Now having said that, it wont always work within the development cycle, I tried it a few weeks ago on my desktop and crashed it immediately. The best thing is to do it when they start the new development.

---

### Post by d3v1150m471c on 2010-03-19
Thanks for all the responses. I'm not looking to upgrade, just see if it's possible to use the lucid security updates.

---

