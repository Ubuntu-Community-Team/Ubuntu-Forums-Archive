---
title: "I Can't Upgrad"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by rustyhonor on 2007-11-13
I'm having problems upgrading.  Here is the error message I get:

Failed to fetch [http://archieve.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://archieve.ubuntu.com/ubuntu/dists/feisty/Release.gpg) Could not resolve 'archieve.ubuntu.com'
Failed to fetch [http://archieve.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://archieve.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archieve.ubuntu.com'
Failed to fetch [http://archieve.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://archieve.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archieve.ubuntu.com'

Has anyone else had this problem?

---

### Post by taurus on 2007-11-13
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by rustyhonor on 2007-11-13
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archieve.ubuntu.com/ubuntu/ feisty main

---

### Post by taurus on 2007-11-13
What if you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the last line, deb [http://archieve.ubuntu.com/ubuntu/](http://archieve.ubuntu.com/ubuntu/) feisty main, to comment it out.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by SeanBlader on 2007-11-13
> **rustyhonor said:**
> 
deb [http://archieve.ubuntu.com/ubuntu/](http://archieve.ubuntu.com/ubuntu/) feisty main

Yup, what he said, the word "archive" is spelled wrong in the last line of your sources list. That would definitely cause an error and explains why the upgrade manager can't find the server.

---

### Post by rustyhonor on 2007-11-13
That seemed to have worked!  Thanks!  BTW, who would misspell 'archieve'? :lolflag:

---

