---
title: "No updates for Feisty yet?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2007-05-13
I'm being told by the update manager that my system is up to date, but I think I remember reading that security patches were released some weeks ago.

My sources were set by default and I have enabled daily checks for all kinds of updates ( securtiy, backports etc.)

The upgrade went well and the system seems fine so I don't know what's wrong here.

I've also noticed that Exaile! isn't in the repository.

Thanks for reading,
Jarlath

---

### Post by bulldog on 2007-05-13
Nothing is wrong,you updated your OS so you should have the newest patches.

---

### Post by mikewhatever on 2007-05-13
Since you seem to have upgraded from the earlier version, your system should indeed be uptodate, because the updates got installed during the upgrade. 
Exail is in the repositories. Try checking that Universe and Miltiverse are enabled under System>Software Sources, or run > sudo aptitude update

---

### Post by QwUo173Hy on 2007-05-13
Okay, so I am up to date. That's great. Thanks. I made a mistake though - it's Deluge that I can't get in the repo, not exail. I have enabled all repos and I ran mikewhatever's command but there' s no difference.

---

### Post by bulldog on 2007-05-14
If it's a bittorrent client it's in the repo's

---

### Post by QwUo173Hy on 2007-05-14
Then I have a problem because I can't get it at all. I disabled all search filters and still can't find it.

Jarlath

---

### Post by bulldog on 2007-05-14
The only repo I have besides the usual ones is this,

##Multimedia
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

Maybe is this the one which provide deluge,I don't know,but give it a try.

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

This one is to import the key.

---

### Post by QwUo173Hy on 2007-05-16
It's not in there either unfortunately. Here's my sources.list in case there's somthing obvious there

> 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://apt.mackers.com/](http://apt.mackers.com/) unstable contrib
# deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main
# deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) edgy-darkmagez games
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
# deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) edgy main
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

