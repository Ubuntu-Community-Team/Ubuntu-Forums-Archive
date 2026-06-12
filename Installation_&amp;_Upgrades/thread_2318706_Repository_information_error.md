---
title: "Repository information error"
date: 2016-03-28
forum: Installation &amp; Upgrades
---

### Post by Federica on 2016-03-28
Last past days I started to get this error while trying to update.

```
W:Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found, W:Failed to fetch [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

```
# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-backports main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) wily-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
```

How can I solve this problem?

---

### Post by deadflowr on 2016-03-28
There is no abiword-stable ppa for 15.10.
You need to remove that from your sources.
Open the app Software and Updates and go to Other software and remove the entries for abiword-stable.
Then when you close Software and Updates, let it run a reload, which will run the apt-get update command for you.

---

### Post by Federica on 2016-03-28
While in S&U, it is best to set the italian or the main server?

Anyway, that solved it, thank you very much!

---

