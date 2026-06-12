---
title: "is it safe for me to upgrade"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by shrndegruv on 2007-12-11
is it safe for me to upgrade from feisty to gutsy with the following sources file?

```


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

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
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse


# for compiz-fusion
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

# for compiz maanger
deb http://gandalfn.club.fr/ubuntu feisty motu

# for ubuntustudio look
#deb http://archive.ubuntustudio.org/ubuntustudio feisty main

# for e17
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17


```

---

### Post by rsambuca on 2007-12-11
I would comment out the bottom (Non-Ubuntu ones) first.

---

### Post by shrndegruv on 2007-12-11
how would I then deal with all packages from those repos??

---

### Post by rsambuca on 2007-12-11
I would remove the packages and then re-install after the upgrade.  That will by far give you the best chance of a successful upgrade.  Just keep the settings folders.

---

### Post by shrndegruv on 2007-12-11
is there any way to know which installed packages came from a specific repo?

---

