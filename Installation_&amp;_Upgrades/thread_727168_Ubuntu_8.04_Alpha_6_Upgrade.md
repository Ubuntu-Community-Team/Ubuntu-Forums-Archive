---
title: "Ubuntu 8.04 Alpha 6 Upgrade"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by EMCGFX on 2008-03-17
Last night I've upgraded from version 7.10 to 8.04 Alpha 6 (from downloaded cd). First impression is really neat ;-) Everything is much cleaner and looks more stable somehow, even do its alpha :) It is worth it, I had only one bug so far but nothing major (of course I've reported it). I think Ubuntu is going into the right direction with looks and features. If any one is steel uses version 7.10 and would like to know or see something specific from 8.04 Alpha 6 let me know I will try to create some screen shots and reviews on here =D Live on the edge is awesome hehe.

---

### Post by EMCGFX on 2008-03-17
Small tip for everybody who is testing 8.04 Alpha 6 like me. You can easily use Ubuntu Guide for Gutsy @ [http://ubuntuguide.org/wiki/Ubuntu:Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") for your Hardy (8.04). Aldo you will need to add some sources latter on as you install some software, you don't need to change your sources.list in the begining of the guide. If any one wants my sources.list file, I will post it here ;-)

---

### Post by -Freak- on 2008-03-19
Please post your sources.list

---

### Post by EMCGFX on 2008-03-19
Here you go buddy ;-)

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha amd64 (20080306.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse


## Custom Added Sources
deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/stemp/ubuntu hardy main
deb-src http://ppa.launchpad.net/stemp/ubuntu hardy main
deb http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy main
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse
```

---

### Post by EMCGFX on 2008-03-23
I've used it couple days, reported some bugs and when I tried to compile/install newest GTK+ package. It stopped booting properly. So, I was forced to re-install into Ubuntu 7.10 stable for now :( Will use the new Ubuntu 8.04 Beta that came out in vmware for testing. I must say it was worth it :) I learned bunch more stuff when I tried using that alpha 6 release.

---

