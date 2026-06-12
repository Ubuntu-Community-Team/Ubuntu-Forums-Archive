---
title: "kernel update &quot;can't be authenticated&quot;?"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by smeaggie on 2008-08-26
Hi,

i'm using ubuntu 8.04 and just got this warning from the update manager: "You are about to install software that **can't be authenticated**! Doing this could allow a malicious individual to damage or take control of your system.".

The updates it complains about are:
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-image-2.6.24-19-generic

all versions are 2.6.24-19.36 wich would be upgraded to 2.6.24-19.41. Now i was expecting the kernel updates to be authenticated? Can I see where this comes from? And most of all: is it known and safe to apply or not?

I'll leave the update manager open for now, waiting for the awnsers :p

Thanks in advance

---

### Post by iaculallad on 2008-08-26
> **smeaggie said:**
> Hi,

i'm using ubuntu 8.04 and just got this warning from the update manager: "You are about to install software that **can't be authenticated**! Doing this could allow a malicious individual to damage or take control of your system.".

The updates it complains about are:
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-image-2.6.24-19-generic

all versions are 2.6.24-19.36 wich would be upgraded to 2.6.24-19.41. Now i was expecting the kernel updates to be authenticated? Can I see where this comes from? And most of all: is it known and safe to apply or not?

I'll leave the update manager open for now, waiting for the awnsers :p

Thanks in advance

Maybe you checked the Proposed updates in your Software Sources. You could install those images. Surely, it would be safe.

---

### Post by smeaggie on 2008-08-26
Thanks for the quick reply, I do not have the proposed updates checked. Could the authentication keys be wrong / messed up (either local or remote)?

---

### Post by iaculallad on 2008-08-26
> **smeaggie said:**
> Thanks for the quick reply, I do not have the proposed updates checked. Could the authentication keys be wrong / messed up (either local or remote)?

I don't think so. In any case, if you're not experiencing any problem with your installation right now, don't update your image files. Just leave it as is.

---

### Post by jamespi on 2008-09-03
i have the same thing - under what circumstances can this situation occur?

here is my sources.list file:
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

