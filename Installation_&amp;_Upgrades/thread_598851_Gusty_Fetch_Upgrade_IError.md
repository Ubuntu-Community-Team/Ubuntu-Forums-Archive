---
title: "Gusty Fetch Upgrade IError"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2007-10-31
Hello, 

I am trying to upgrade from Fiesty (7.04) to Gusty (7.10). Unfortunately, I experience some issues. First, when I start the upgrade, the system fetches files a bunch of times. It will say 1 out of 76 up to 76 out of 76 and then repeat multiple times, reports a complete fetch, fetches 2 more files, fetches 76 files again, then fails. Its failure message is an HTTP 302 code. I thought to wait and try again-302 means that the resource has moved for a temporary period. That was a few days ago, I now tried again and there was the error again.

```
Failed to fetch http://www.osrts.info/~tvo/deb/dists/edgy/spring/binary-i386/Packages.gz 302 Found
```

Seeing as this is an isolated incident, and no one else seems to have this problem, something must be wrong with my computer. Why it would return a non-existent stat code I do not know.

Anyone have any ideas?

-Dylan

EDIT: I noticed this is not a Gusty update fetch, hence the reason only I experience it. Any way to hold it back while I upgrade, or must I uninstall spring?

---

### Post by taurus on 2007-10-31
Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by Dylnuge on 2007-10-31
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

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://www.osrts.info/~tvo/deb edgy spring

```

Yes, I use Automatix. It was a quick way to get my system running back when I installed 6.10, and I have not used it since. The repo with the problem is last. Should I comment it out for the time being?

---

### Post by taurus on 2007-10-31
Actually, you want to comment out all these lines at the end by placing a # in front of them.

```
gksudo gedit /etc/apt/sources.list
```

```

#AUTOMATIX REPOS START

#deb http://www.getautomatix.com/apt feisty main

#deb http://archive.canonical.com/ubuntu feisty-commercial main

#deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

#deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
#deb http://www.osrts.info/~tvo/deb edgy spring

```

Save it and run

```
sudo apt-get remove automatix2
sudo apt-get update
```
Now, see if you can upgrade it to Gutsy.

---

### Post by Dylnuge on 2007-10-31
Already started with just one line commented out. Automatix survived the last upgrade, iut should survive this one. Hopefully. If not, my data is on a seperate part and backed up.

---

