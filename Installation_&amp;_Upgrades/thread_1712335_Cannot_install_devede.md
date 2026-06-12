---
title: "Cannot install devede"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by drz4007 on 2011-03-22
Hello. I am using Ubuntu 10.04 amd64 and i try to install devede, but it doesn't install because mencoder must also be installed, but to install mencoder mplayer must be installed, but mplayer has many conflicts with many programs i have installed like VLC and audacity. Does anybody know why this happens and what I should do? Thanx a lot.

---

### Post by Dutch70 on 2011-03-22
Have you tried to install it from Synaptic? That should include all of the dependencies.

---

### Post by drz4007 on 2011-03-22
yes. Both synaptic and terminal. The same result.

---

### Post by coffeecat on 2011-03-22
I have routinely installed DeVeDe, mplayer, VLC and Audacity  in all the installations I have done since before 10.04 and I haven't seen this. There are no conflicts in the applications you mention, nor in their dependencies, so long as you are installing them from the official repositories. Which makes me wonder if you have any PPA and/or 3rd party repositories enabled. 

Have you enabled any PPA repositories?

---

### Post by drz4007 on 2011-03-22
**I think so. These are my sources**:


# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) lucid main
deb [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) lucid main
deb [http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu](http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu](http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu) lucid main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-proposed restricted main multiverse universe

---

### Post by coffeecat on 2011-03-22
These:

> **drz4007 said:**
> deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) lucid main
deb [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) lucid main
deb [http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu](http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu](http://ppa.launchpad.net/ferramroberto/lfflavidemux/ubuntu) lucid main universe

... are non-standard repositories. You also need to check in the /etc/apt/sources.list.d/ folder. Some PPA repositories and other 3rd party set up their own *.list files in that folder. 

I'm not familiar with any of those repositories, but one of the non-standard ones must be responsible for the conflict. You'd need to check your installed VLC and audacity as well as their dependencies to see whether any of them have come from a non-standard repository. Then you'll know where the problem might be.

Just to show you that if you restrict yourself to the standard Ubuntu repositories, the applications you list can co-exist in 10.04. The screenshot is my AMD64 10.04 Sound and Video menu.

---

### Post by drz4007 on 2011-03-23
After experimenting I found that the VLC ppa (the one provided by the VLC site for UBUNTU 10.04) was conflicting with DEVEDE. Is there a way to fix that or I have to settle with VLC version 1.0.6?

---

### Post by drz4007 on 2011-03-23
After more experimenting I finally installed both VLC (the latest version) and DEVEDE. But I had to do alot by hand. I had to update mencoder by hand. I just can't understand why that happened... Usually everything is done automatically. I mean depedencies, etc...

---

