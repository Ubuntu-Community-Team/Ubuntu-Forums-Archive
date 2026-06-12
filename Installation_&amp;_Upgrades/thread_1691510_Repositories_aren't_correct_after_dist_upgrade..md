---
title: "Repositories aren't correct after dist upgrade."
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by ferulebezel on 2011-02-20
I want to install Suns java.  For instructions I found this:

> To install (Sun) Java in Ubuntu 10.10 Maverick Meerkat you'll have to enable the Partner repository: open Ubuntu Software Center and go to Edit > Software Sources, then on the "Other Software" enable the Partner repository (it should be the first on the list; it looks like this: "http://archive.canonical.com/ubuntu maverick partner".).

Then, click "Close" and when asked, click "Reload" and finally install Sun Java6 in Ubuntu 10.10 by searching for it in Ubuntu Software Center.

It turn out that the maverick partner repository isn't there but the karmic still is.  Apparently the dist upgrade didn't upgrade that.

How do I do it?

---

### Post by oldos2er on 2011-02-20
Can you post the output of **cat /etc/apt/sources.list** ?

---

### Post by ferulebezel on 2011-02-23
> **oldos2er said:**
> Can you post the output of **cat /etc/apt/sources.list** ?

Here ya go:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.2)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted multiverse
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
```

---

### Post by oldos2er on 2011-02-23
Change the partner repository lines to 

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner 
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner

then run **sudo apt-get update**

---

### Post by ferulebezel on 2011-02-24
Thanks.  That worked.

I'm wondering If I'm going to have to do that whenever I do a dist upgrade.

I installed Suns java but I get this.

```
] java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.5) (6b20-1.9.5-0ubuntu1)
OpenJDK Server VM (build 19.0-b09, mixed mode)
```

Why

---

### Post by oldos2er on 2011-02-24
If you want Sun java to be the default, run ```
sudo update-alternatives --config java
``` to select it.

---

