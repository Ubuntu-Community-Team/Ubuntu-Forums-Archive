---
title: "Target Sources is configured multiple times ...."
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by michael351 on 2022-08-31
I have the following warning when updating Ubuntu (22.04):

W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7
W: Target Sources (restricted/source/Sources) is configured multiple times in /etc/apt/sources.list:2 and /etc/apt/sources.list:7

Below is my sources.list file:
[INDENT=2]# deb cdrom:[Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819)]/ focal main restricted
deb-src [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy main restricted
deb-src [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-updates main restricted
deb-src [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-backports main restricted universe multiverse
deb-src [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-backports main restricted universe multiverse


deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-security main restricted
deb-src [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-security main restricted multiverse universe
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://mirror.team-cymru.com/ubuntu/](http://mirror.team-cymru.com/ubuntu/) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
[/INDENT]

---

### Post by jeremy31 on 2022-08-31
Edit the file and comment out line 7, change from
```
deb-src http://mirror.team-cymru.com/ubuntu/ jammy restricted multiverse universe
```
To
```
#deb-src http://mirror.team-cymru.com/ubuntu/ jammy restricted multiverse universe
```
Then see if updates work

---

### Post by michael351 on 2022-09-01
That did it! 
Thank you!!

---

### Post by mIk3_08 on 2022-09-01
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

