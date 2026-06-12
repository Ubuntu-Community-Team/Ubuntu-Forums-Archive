---
title: "Sources missing in sources list?"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-09-05
Hi all. Was looking around at something else completely last night and noticed something at HermanZone. In an example of his sources list, he seemed to have a bunch of sources that I don't have. It might explain why I am rarely getting asked to update etc. Don't know what happened or where they might have gone but ***gksudo gedit /etc/apt/sources.list*** gives me this:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy main multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe

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
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main multiverse restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
deb http://ubuntusatanic.org/hell hardy main
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main universe multiverse restricted
```What should I have in there? The missing ones were at the bottom of this list and regarded security updates. :-k

ps: I never use KDE so that is why that entry at the bottom section in the middle is hashed out.

---

### Post by Shazaam on 2008-09-06
Here is mine (the ppa ones are extra)...
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy main multiverse restricted universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main multiverse restricted universe
deb http://ppa.launchpad.net/daou/ubuntu hardy main
deb-src http://ppa.launchpad.net/daou/ubuntu hardy main
deb http://ppa.launchpad.net/doctormo/ubuntu hardy main
deb-src http://ppa.launchpad.net/doctormo/ubuntu hardy main
```

---

### Post by cdtech on 2008-09-06
You can go into "System > Admin > Software Sources" and check the first four under "Ubuntu Software" which will add the extras for you. If you messed up you list you can reinstall it from the Live CD.

**Update::.**
This is all I have in mine, if it helps ya.
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

deb http://apt.wicd.net hardy extras
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main

deb http://ubuntu.citadel.org/ubuntu/ hardy main

# deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/superm1/ubuntu hardy main
deb-src http://ppa.launchpad.net/superm1/ubuntu hardy main
```

---

### Post by Bucky Ball on 2008-09-06
Thanks to both of you. Will play around with that and see how I go. :)

---

