---
title: "E: Type 'usage:' is not known on line 54 in source list /etc/apt/sources.list"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by terrapin893 on 2010-01-23
So Ive seen some fixes for this on the net but they all seem to be specific to the particular user's sources.list . . . . so I'll post mine here, and give thanks in advance.  

```

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
usage: sudo [-n] -h | -K | -k | -L | -V | -v 
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

```

Here is Line 54 
```
usage: sudo [-n] -h | -K | -k | -L | -V | -v 
```

---

### Post by Elfy on 2010-01-23
Open the file to edit

```
gksudo gedit /etc/apt/sources.list
```

Delete all the 
> 
usage: sudo [-n] -h | -K | -k | -L | -V | -v 
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

save and close then run

```
sudo apt-get update
```

post back if there are errors

your sources should only have lines starting with deb, deb-src or #

---

### Post by terrapin893 on 2010-01-23
Beautiful, thanks very much.  I was wondering where the syntax error was.  I had tried to do a manual install of cairo-dock and it didn't go as planned.  

Again, Thanks!

---

