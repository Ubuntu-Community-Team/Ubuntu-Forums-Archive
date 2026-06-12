---
title: "update gives &quot;duplicate sources&quot; warning"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by mringer on 2015-11-26
In previous threads, people were urged to supply /etc/apt/sources.list, so here it is. Sorry, it does look rather a mess:

```
# deb cdrom:[Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main multiverse restricted universe
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports restricted universe multiverse main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports restricted universe multiverse main #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted multiverse universe main #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
```


Also the contents of /etc/apt/sources.list.d:

google-earth.list:

```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
```


 ubuntu-sdk-team-ppa-trusty.list:

```
deb [http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu) trusty main
```


Thanks for any advice.

---

### Post by ian-weisser on 2015-11-26
> **mringer said:**
> Sorry, it does look rather a mess:

Yes, a bit, with lots of duplicate entries.
Your should clean that up, and remove the duplicate entries while you're at it.

Are you asking how to find the duoplicate entries?
Or are you asking what to do about the duplicate entries?
Or are you asking how to clean up?

Hint: Your huge sources.list file, once you eliminate all the ancient barnacles and duplicates and comments, essentially boils down to this:
```
deb http://gb.archive.ubuntu.com/ubuntu/ trusty restricted multiverse universe main
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty restricted multiverse universe main

deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates restricted multiverse universe main
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates restricted multiverse universe main

deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports restricted universe multiverse main
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports restricted universe multiverse main

deb http://security.ubuntu.com/ubuntu trusty-security restricted universe multiverse main
deb-src http://security.ubuntu.com/ubuntu trusty-security restricted universe multiverse main

deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

---

### Post by mringer on 2015-11-27
> **ian-weisser said:**
> 

Are you asking how to find the duoplicate entries?
Or are you asking what to do about the duplicate entries?
Or are you asking how to clean up?



I suppose, a bit of all 3. Thank you, I think I know what to do now. I will try to mark this
as solved.

---

