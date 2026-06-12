---
title: "repositories source list"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by mpcadel on 2010-02-12
I am new to using Ubuntu and I made some stupid mistake which I am still trying to figure out what it was, but I did delete the source list, it is now an empty file XDXDXD

I tried to find any copy of the list but couldn't find, so can somebody post me the original repositories list that come with Ubuntu?

Thanks

---

### Post by RedSingularity on 2010-02-12
Here is the one that comes with ubuntu...............

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

---

### Post by sisco311 on 2010-02-12
You are using Karmic, right?
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

---

### Post by wojox on 2010-02-12
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by sisco311 on 2010-02-12
or go to: System -> Administration -> Software Sources -> 
[list][*]*Ubuntu Software* tab and enable the main (optionally the universe, restricted, multivers & source code) repo
[*]*Updates* tab and enable karmic-security & karmic-updates
[/list]

---

### Post by mpcadel on 2010-02-13
Thanks a lot of guys for the help.
But here is what I am getting :

I am launching the sources list from the terminal, then suddenly when I past the list and try to close and save
it says 
"Could not find the file /home/adel/ect/apt/sources.list.
Please check that you typed the location correctly and try again."

I tried different lists from what was posted above and all got me the same message :(

---

### Post by mpcadel on 2010-02-13
Oh never mind.
I got it solved, thanks for all who have posted :)

---

