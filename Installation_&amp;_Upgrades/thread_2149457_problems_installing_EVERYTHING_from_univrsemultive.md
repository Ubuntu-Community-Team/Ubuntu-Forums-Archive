---
title: "problems installing EVERYTHING from univrse/multiverse after fresh 13.04 install"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by killer62491 on 2013-05-28
i took a look around the forums first to make sure this wasn't a previously mentiond/resolved issue. it appears im either the first to have this extremely wierd problem so i'll shoot off the details to see if i can get help. 

First off: i'd installed 13.04 onto several liveUSB's, and NONE allowed me to install packages from univrse or multiverse repo's once they were booted into. i checked my sources.list file like one would normally do, but nothing's off in there. ill post the contents in a bit once i get to it. 

Second off: after looking at the two drives i've used initially, i noticed that oddly, one if running as if it were created using unetbootin judging by the bootsplash, even though i didn't...

so heres the sources.list contents if anyone can help...

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

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
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```

also, i never did much with source adding before, so i honestly might've missed a huge issue while not seeing it at all :(

[EDIT:] wow nevermind... i found a fix using google to search for other repository problems after a fresh install, this made me feel quite dumb, as it was a ridiculously easy fix. thanks if you posted a reply while i was editing though :D:D

---

### Post by TheFu on 2013-05-29
Could you please mark this post as "SOLVED" with the link - this would have saved lots of people looking to help from reading it.

---

