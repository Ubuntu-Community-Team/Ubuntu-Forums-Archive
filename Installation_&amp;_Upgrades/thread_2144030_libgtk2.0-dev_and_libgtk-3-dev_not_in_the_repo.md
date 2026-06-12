---
title: "libgtk2.0-dev and libgtk-3-dev not in the repo?"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by Naddiseo on 2013-05-10
I'm trying to install a package that provides <gtk/gtk.h> which
"http://packages.ubuntu.com/search?searchon=contents&keywords=gtk%2Fgtk.h&mode=exactfilename&suite=raring&arch=any"
reports as libgtk2.0-dev and libgtk-3-dev, but I'm unable to install
them. As far as I can tell, I have all the necessary repositories
enabled, and my system is up-to-date.

$ apt-cache policy libgtk2.0-dev
N: Unable to locate package libgtk2.0-dev
N: Couldn't find any package by regex 'libgtk2.0-dev'

$ apt-cache policy libgtk-3-dev
libgtk-3-dev:
  Installed: (none)
  Candidate: (none)
  Version table:

My apt sources:
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20111129.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20111129.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb http://archive.ubuntu.com/ubuntu raring-proposed restricted main multiverse universe
deb-src http://extras.ubuntu.com/ubuntu raring main

```

---

