---
title: "[SOLVED] Update/Package dowloads are failing - Help"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by skippi90 on 2008-02-08
My update manager and synaptic package manager is failing to download files - usually with the message that it "Failed to fetch"

Any ideas how to fix this?

I need a quick answer if possible and every response is greatly appreciated.

Thanks
----------------


Stevie

---

### Post by kellemes on 2008-02-08
You have internet at all?

---

### Post by skippi90 on 2008-02-08
Yes. I'm using it now with Firefox. I downloaded the source files OK but I can't get the updates or programs to download.

---

### Post by skippi90 on 2008-02-08
Anyone?

Here is my sources list:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://th.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://th.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://th.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://th.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://th.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://th.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
```

---

### Post by skippi90 on 2008-02-08
Could it be a DNS Issue?

I have a D-Link router and my ISP is BT. In networking, under DNS, the only adress it has is 192.168.1.1

---

### Post by skippi90 on 2008-02-08
I seem to have fixed it. The files are now finally downloading.

I deleted the 192.168.1.1 DNS address and added 208.67.222.222 and 208.67.220.220

:)

---

