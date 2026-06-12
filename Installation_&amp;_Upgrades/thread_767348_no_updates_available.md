---
title: "no updates available"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by fela on 2008-04-25
Hi
I've been using hardy beta for a couple of weeks, but when hardy was released (yesterday) i stopped getting updates available. Even when i ran ```
sudo apt-get update
``` there were still no updates available, either in sudo apt-get upgrade or update-manager so i still get the same bugs that were in the beta, such as no trash can. (and the 'development version' grub menu entries). Here is my /etc/apt/sources.list:

```
me@aquabuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080318.1)]/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

## for e17
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe #Added by software-properties
# deb http://cafelinux.org/Downloads/oz-os tinwoodman main


deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
me@aquabuntu:~$
```

That last deb line is something i added in pure frustration trying to get my updates back. It didn't help one bit.

I really appreciate any help anyone can give, i am at my wits end on this.

---

### Post by Pumalite on 2008-04-25
If you have kept up with the updates, you have Final Release for 38 HRS now and won't be getting updates for a while. Packages are locked for the release. Post:
cat /etc/lsb-release

---

### Post by fela on 2008-04-25
> **Pumalite said:**
> If you have kept up with the updates, you have Final Release for 38 HRS now and won't be getting updates for a while. Packages are locked for the release. Post:
cat /etc/lsb-release
```

me@aquabuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
me@aquabuntu:~$ 
```

I know that i haven't been getting updates that i should have, as i know someone that has been using hardy beta but he got loads of updates on the release day (whereas i got none whatsoever)

thanks for reply anyhow

fela

---

### Post by Joeb454 on 2008-04-25
Chances are he didn't keep it fully up-to-date.

I got 0 updates from around 11am GMT on the 23rd of April. Believe me I checked. And I kept my install up-to-date as and when updates became available :)

---

### Post by jerrykenny on 2008-04-25
Hopefully its just a temporary thing thing fela . . . . do you still have ubuntu-desktop metapackage installed ?  maybe it was removed if you uninstalled one component . . . i dont think it'd make any real odds mind you

How about apt-get dist-upgrade ?

---

### Post by Pumalite on 2008-04-25
> **fela said:**
> ```

me@aquabuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
me@aquabuntu:~$ 
```

I know that i haven't been getting updates that i should have, as i know someone that has been using hardy beta but he got loads of updates on the release day (whereas i got none whatsoever)

thanks for reply anyhow

fela

Your lsb-release shows that you have the Final Release.

---

### Post by fela on 2008-04-25
> **Joeb454 said:**
> Chances are he didn't keep it fully up-to-date.

I got 0 updates from around 11am GMT on the 23rd of April. Believe me I checked. And I kept my install up-to-date as and when updates became available :)

that explains it. I always keep to the latest updates. Maybe in a few days i'll get like 1000 updates available or something...

---

### Post by Pumalite on 2008-04-25
I doubt it

---

### Post by fela on 2008-04-25
> **jerrykenny said:**
> Hopefully its just a temporary thing thing fela . . . . do you still have ubuntu-desktop metapackage installed ?  maybe it was removed if you uninstalled one component . . . i dont think it'd make any real odds mind you

How about apt-get dist-upgrade ?

no, i have ubuntu-desktop and dist-upgrade didn't offer any upgrades. I reckon i am actually on the latest updates (and update manager hasn't been lying)...maybe we're in a period of calm before the rush of bug fixes.although i don't seem to remember that happening with gutsy anyway...i'll mark this thread solved.

EDIT: they seem to have moved it...where is the solved button?

---

### Post by Joeb454 on 2008-04-25
I'm not sure where the solved button lives anymore :p

And chances are you won't get any updates for a while yet :)

---

### Post by Pumalite on 2008-04-25
> **fela said:**
> no, i have ubuntu-desktop and dist-upgrade didn't offer any upgrades. I reckon i am actually on the latest updates (and update manager hasn't been lying)...maybe we're in a period of calm before the rush of bug fixes.although i don't seem to remember that happening with gutsy anyway...i'll mark this thread solved.

EDIT: they seem to have moved it...where is the solved button?

Use the 'Thread Tools'

---

### Post by potrzebie on 2008-04-26
Yeah, I think we are in the post-release lull, you aren't missing out on any updates. I installed the release candidate last weekend, and there were a flurry or updates for a day or two, but the evening before the release date I had just one package update ([eterm]("http://packages.ubuntu.com/hardy/eterm")) and that's been it so far. This is it. You're running Hardy Heron. Enjoy.

---

### Post by fela on 2008-04-26
> **Pumalite said:**
> Use the 'Thread Tools'

no, they've changed the whole forum's layout around...and moved the solved button so none of us know where it is anymore.

---

