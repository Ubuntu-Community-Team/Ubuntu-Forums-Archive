---
title: "Problems with update manager after Hardy upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Theo148 on 2008-04-30
I just upgraded a friend's computer from Gutsy to Hardy via the alternate install CD. Everything went fine and the new system works perfectly, except for one quirk: the update manager insists that the computer needs to install 106 updates, many of which do not seem to be valid for his system (for example the Xubuntu artwork is included in the list event though the computer is running a standard Ubuntu distro).

I have checked the software sources and everything seems valid for Hardy, so I'm pretty sure that it has something to do with an old list of updates that somehow got picked up by the Update Manager. Is there a command I can run to clear the updates cache or whatever (or is there any other way I can solve the problem)?

---

### Post by Pumalite on 2008-04-30
Post:
cat /etc/apt/sources.list

---

### Post by Theo148 on 2008-04-30
```
#

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb http://my.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://my.archive.ubuntu.com/ubuntu/ hardy universe
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://my.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://my.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by Pumalite on 2008-05-01
Your sources.list is fine. The Xubuntu artwarks is offered in many repos. You don't have to accept it.

---

### Post by Theo148 on 2008-05-01
Hmm... I wasn't under the impression that it would be listed as an update.

---

### Post by Pumalite on 2008-05-01
I haven't seen it as an update either. Your updates are offered to you according to what you have installed.

---

### Post by Theo148 on 2008-05-02
Hmm... well looking at the list of updates, I can see a whole lot of packages that were once installed on the computer, but removed during the Hardy upgrade. I guess we can just put up with it for now. :P

---

### Post by dimitarc on 2008-06-03
I have similar problem with this issue. When I will try to check for updates or try to install updates it just crash. Does not do anything, you can exit it, you need to kill the process from "System monitor."

I get this problem after I upgraded on 8.04 from 7.10 via internet. I installed my desktop PC from the cd I ordered and I don't have this problem there. But my lap top is my main pc so please help. I don't want to use not updated system.

Thank you in advance.

---

