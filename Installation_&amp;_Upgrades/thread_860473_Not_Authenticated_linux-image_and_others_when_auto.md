---
title: "Not Authenticated linux-image and others when autoupdating Gutsy"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by Orthanc on 2008-07-15
This morning I attempted to run the Update manager to bring my Gutsy installation up to date. However I got the error:

"You are about to install software that **can't be authenticated**! Doing this could allow a malicious individual to damage or take control of your system."

The packages it lists as not authenticated are:
[LIST]
[*] linux-image-2.6.22-15-generic
[*] libpcre3
[*] libpcrecpp0
[*] linux-headers-2.6.22-15
[*] linux-headers-2.6.22-15-generic
[/LIST]

I haven't received this message before, and the linux-image and linux-header ones seem like fairly core parts of the system. Does anyone know if there is a problem with the signatures for these libraries (or whatever's being used for authentication)?

My /etc/apt/sources.list follows
```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Pumalite on 2008-07-15
Post:
uname -a

---

### Post by Orthanc on 2008-07-15
uname -a:
```

Linux edwardc 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux

```

---

### Post by Pumalite on 2008-07-15
You already seem to have the update offered to you.

---

### Post by Orthanc on 2008-07-15
So any idea why update manager thinks I don't? And any way I can fix this so it doesn't prompt me about these updates?

I haven't done anything fancy on this box, basically just install from Gutsy CD then install updates as prompted. I haven't done anything at all with the kernal that would get it out of sync with APT as far as I'm aware.

---

### Post by Pumalite on 2008-07-16
Post:
cat /etc/apt/sources.list

---

### Post by Orthanc on 2008-07-16
/etc/apt/sources.list is in the first post of the thread.

Here it is again:
```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb http://mirror/archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://mirror/security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Pumalite on 2008-07-16
I would go ahead and accept the updates. Your repos are all legitimate.

---

### Post by Orthanc on 2008-07-16
Trying again this morning, it's not warning about the not-authenticated any more anway.

Guess it was just a transient condition. Thanks for all your help.

---

