---
title: "Update Manager crashes after unsuccessful upgrade to 13.04"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by obsidianW on 2013-05-06
And this is not only Update Manager, but also Ubuntu Software Center and anything dealing with software sources...

... this is what I assume after a huge research done on Ubuntu Forums and Google. In the end of day I could not find any solution to solve this problem.

Just a quick say how it all began:

I saw update available to Ubuntu 13.04 in Update Manager. So I clicked the button and upgrading process started. It was all ok till a moment I got an error I cannot remember at the moment. Something failed for sure. And since then I have problems with anything what accesses software source lists. I tried to look in the files but did not see anything suspicious. I present files below:

```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://je.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://je.archive.ubuntu.com/ubuntu/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://je.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://je.archive.ubuntu.com/ubuntu/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://je.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://je.archive.ubuntu.com/ubuntu/ raring universe
deb http://je.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://je.archive.ubuntu.com/ubuntu/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://je.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://je.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://je.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://je.archive.ubuntu.com/ubuntu/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://je.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://je.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb http://je.archive.ubuntu.com/ubuntu/ raring-proposed restricted main multiverse universe
deb-src http://extras.ubuntu.com/ubuntu raring main
```

This is it.

I have no idea where and how to bite it.

Any help guys will be much appreciated.

---

### Post by matt_symes on 2013-05-06
Hi

Welcome to the forums.

Open a terminal and type

```
sudo apt-get update
```

If it fails, post the output back here.

If it suceeds then type

```
sudo apt-get upgrade
```

Any error message post them back here.

If that suceeds type

```
gksudo software-center
```

Try to install something and then post back the output from the terminal.

Kind regards

---

### Post by obsidianW on 2013-05-07
Ok... So I am much confused now.


I tried all above commands in terminal before I posted here... all ended up with failure. I started again with the first one you asked for in your post... and it went through! So I quickly checked Software Center - is now working, the same with Update Manager - currently it is PARTIALLY updating after a message about last update being corrupted or some packages are incorrect. It showed me list of updates available, but most of them where forced unticked. I am now updating the ones ticked.


I will let you know how it went a bit later as my connection is slow.


Thank you for your reply anyway. You were very reliable. I hope problems will be gone after the process finish.


Kind regards.

---

