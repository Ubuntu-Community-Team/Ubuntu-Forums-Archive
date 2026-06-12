---
title: "do-release-upgrade from 14.04 fails"
date: 2019-04-18
forum: Installation &amp; Upgrades
---

### Post by honeycombs_big_yahyahyah on 2019-04-18
Hi all,

Finally trying to take the leap from 14.04 on my server installation.  However, the process is having issues.  Specifically, after running do-release-upgrade, I get:


during the first pass through the apt sources, it reports this:
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
Building data structures... Done


Updating repository information


Third party sources disabled


Some third party entries in your sources.list were disabled. You can
re-enable them after the upgrade with the 'software-properties' tool
or your package manager.


To continue please press [ENTER]
```

Then, after pressing enter, it reports this:
```
, E:Some index files failed to download. They have been ignored, or
old ones used instead.




Restoring original system state


Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command terminated with exit status 1 (Thu Apr 18 10:29:33 2019) ===
```

Then it just goes back to where I was previously.  Any thoughts?  I suspect it might have something to do with my apt sources, which I include below.  Any thoughts greatly appreciated!

Thanks,
Allie

/etc/apt/sources.list:
```
# deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

# deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
# deb http://security.ubuntu.com/ubuntu trusty-security main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main


deb http://download.webmin.com/download/repository sarge contrib
deb http://webmin.mirror.somersettechsolutions.co.uk/repository sarge contrib
```

---

### Post by Bashing-om on 2019-04-18
honeycombs_big_yahyahyah; Ouch !

Hoo boy ...
1st up is a mixed repo .. No No :
[https://wiki.debian.org/DontBreakDebian](https://wiki.debian.org/DontBreakDebian)

As you have those sarge repos: [http://download.webmin.com/download/repository/Release](http://download.webmin.com/download/repository/Release)

I have no inkling of what may be added and/or changed. Maybe just maybe remove the sarge software and delete the source; then try the release upgrade again ?

[INDENT][INDENT]maybe possible
[/INDENT][/INDENT]

---

