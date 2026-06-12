---
title: "Can't Upgrade to 7.10"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by whistlerspa on 2007-10-26
I tried to update my Synaptic prior to distribution upgrade. 
The following error comes up.

[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

When I tried the upgrade subsequently from the Alternative disk - as recommended due to having an ATI 9600 video card guess what - got the same error as the program tried to download updates.

What is this package and how do I handle it? Same error also occurs from apt-get update terminal command.

A little further research seems to indicate it's got something to do with fglrx restricted ATI drivers so what do i do about this

---

### Post by taurus on 2007-10-26
Why don't you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of that line regarding your fglrx to comment it out.  Save it and see if you can update your machine now.

---

### Post by whistlerspa on 2007-10-26
> **taurus said:**
> Why don't you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of that line regarding your fglrx to comment it out.  Save it and see if you can update your machine now.


Thanks just tried that but interestingly the line is not there to edit out.

---

### Post by taurus on 2007-10-26
Post your /etc/apt/sources.list here if you're not sure.

```
cat /etc/apt/sources.list
```

---

### Post by whistlerspa on 2007-10-26
OK here goes

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)

#AUTOMATIX REPOS START


deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security restricted
#AUTOMATIX REPOS END
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/

---

### Post by taurus on 2007-10-26
You need to be a little more careful with your /etc/apt/sources.list.  It is not a good idea to mix different repos in there.  You are running Feisty but you have an Edgy repo so remove it or comment it out.

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of these lines at the bottom of it.

```

#deb http://wine.budgetdedicated.com/apt edgy main

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs

#AUTOMATIX REPOS START

#deb http://archive.canonical.com/ubuntu feisty-commercial main

#deb http://archive.ubuntu.com/ubuntu/ feisty-updates universe

#deb http://archive.ubuntu.com/ubuntu/ feisty-security restricted
#AUTOMATIX REPOS END
#deb http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu feisty/

```
Save it and then run

```
sudo apt-get update
```
See if you can upgrade your machine now.

---

### Post by whistlerspa on 2007-10-30
Thank you tried that and was able to upgrade  - a few bugs? though.

emacs and cedet dependency problems

---

### Post by whistlerspa on 2007-11-04
As an epitaph tried to upgrade a laptop to Vista from XP today. After following the upgrade adviser to the letter (with recommended updates, uninstalls et al) - guess what 

Blue screen of death and miserable failure. A mate had the same experience today as well.

:lolflag:

---

