---
title: "[SOLVED] Can't Install Gnome-Common"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by alsamman on 2008-01-28
Hi, I am trying to install AWN Curves and the first step requires me to install gnome-common. This I cannot do as I get the following error:
gnome-common:
Depends: libtool but it is not going to be installed

then when I try to install libtool:
libtool:
Depends: libc6-dev but it is not going to be installed or
libc-dev

...and then libc6-dev
libc6-dev:
Depends: libc6 (=2.6.1-1ubuntu10) but 2.7-5ubuntu1 is to be installed

any ideas?

---

### Post by Partyboi2 on 2008-01-28
are you manually trying to install these packages or are you using synaptic or apt-get?

---

### Post by alsamman on 2008-01-28
> **Partyboi2 said:**
> are you manually trying to install these packages or are you using synaptic or apt-get?

both, and they both yield the same error

---

### Post by jsonder on 2008-01-28
Strange.

It installed fine just now on a Dell Inspiron 1505 running Ubuntu 7.10 (updates are current) using the package manager.

---

### Post by Partyboi2 on 2008-01-28
What version of ubuntu are you running?
Edit: Nevermind I see the info in your sig.

---

### Post by Partyboi2 on 2008-01-28
>  Depends: libc6 (=2.6.1-1ubuntu10) but 2.7-5ubuntu1 is to be installed
libc6 (=2.6.1-1ubuntu10) is gusty
libc6 2.7.5ubuntu1 is hardy
can you post your source.list please
```
cat /etc/apt/sources.list
```

---

### Post by alsamman on 2008-01-28
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
deb http://packages.medibuntu.org/ gutsy free non-free

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://giss.tv/~vale/ubuntu32 ./
deb-src http://giss.tv/~vale/ubuntu32 ./

```

---

### Post by Partyboi2 on 2008-01-29
Your source.list looks fine. I just install awn without gnome-common installed on my system. So I suggest trying, one line at a time
```
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by alsamman on 2008-01-29
> **Partyboi2 said:**
> Your source.list looks fine. I just install awn without gnome-common installed on my system. So I suggest trying, one line at a time
```
wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc)
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

i have awn on my computer too without awn its the awn CURVES that i want to install and that is what requires me to install gnome-common and i just dont understand why i cant do so:confused:](*,)

---

### Post by alsamman on 2008-01-29
bump

---

### Post by Partyboi2 on 2008-01-29
Having a look at your source.list again I don't think you have all the repos enabled Open up software sources (System>Admin>Software Sources) and on the first tab make sure all of them are ticked except source code. then close and try again.

---

### Post by alsamman on 2008-01-30
still doesnt work but you see the weird thing is, is that my version of libc6 is 2.7 and it doesnt allow me to reinstall it i can only remove it and if i do it is going to remove a bunch of other applications with it

---

