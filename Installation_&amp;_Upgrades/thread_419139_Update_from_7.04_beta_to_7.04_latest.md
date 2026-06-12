---
title: "Update from 7.04 beta to 7.04 latest"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by timothyp on 2007-04-22
Hi,

I installed ubuntu 7.04 some time ago (beta) and I'm quite happy with it.
My question is whether or not I need to do something in order to make it 
update to the final version?
As  I no longer seem to be receiving any updates.

This has been the case since shortly before the official release,
on multiple systems we manage.

This is my sources list

```

#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070228.1)]/ feisty main restricted

#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Alpha i386 (20070228.1)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main


```

---

### Post by jfinkels on 2007-04-22
There were very few, if any, updates in the few days prior to the final release of feisty, and there haven't been many, if any at all, in the few days following the release. I think.

---

### Post by timothyp on 2007-04-22
Ok, and /etc/issue shows the right version (just figured that one out :p) so thank you for your quick reply.

---

