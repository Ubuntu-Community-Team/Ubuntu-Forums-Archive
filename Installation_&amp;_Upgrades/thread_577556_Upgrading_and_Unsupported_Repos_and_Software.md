---
title: "Upgrading and Unsupported Repos and Software"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by navneeth on 2007-10-16
Hi,
 Like most of you, if not *all* of you, I'm eagerly awaiting the 18th. I will upgrade only a day or two after the official final version is out. But I'm just preparing to do my first upgrade (as opposed to a fresh install as in the last two times.) I have read that it is not safe to have unsupported repos in the sources.list file while upgrading. I also read in a thread, that it is best to comment out the thrid-party repos. 

Now, I have installed a couple of things from Automatix, and use a two or three repos (Sky Chart astronomy program, the latest version of Amarok, etc..). What do I do with these programs? Do I uninstall them?

**For you reference**
```
navneeth@ubuntu:/etc/apt$ ls
apt.conf.d                        sources.list_backup_200707310134
secring.gpg                       sources.list_backup_200708221848
sourcesbackup.list                sources.list_backup_200710122305
sources.list                      sources.list_backup_200710140132
sources.list~                     sources.list_backup_200710140140
sources.list_backup_200704240011  sources.list_backup_200710141401
sources.list_backup_200704240221  sources.list_backup_200710141404
sources.list_backup_200704260246  sources.list_backup_200710141408
sources.list_backup_200704262339  sources.list_backup_200710141603
sources.list_backup_200705110151  sources.list.d
sources.list_backup_200705150157  trustdb.gpg
sources.list_backup_200705182005  trusted.gpg
sources.list_backup_200705301847  trusted.gpg~
sources.list_backup_200707310108

```

I don't know how so many backups came to be.

```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://kubuntu.org/packages/amarok-145 edgy main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://kent.dl.sourceforge.net/sourceforge/ skychart/


#MEDIBUNTU

#deb http://medibuntu.sos-sts.com/repo feisty free nonfree
```

I don't remember installing anything from Medibuntu. I must've changed my mind or something.

---

### Post by navneeth on 2007-10-17
Anyone?

---

### Post by blakeg on 2007-10-17
When I try to go to [http://medibuntu.sos-sts.com/repo](http://medibuntu.sos-sts.com/repo), I get an http 403 error. So I would assume it's safe to remove that one or comment it out.

I would also assume it would be alright to delete the old backups of your sources.list.

As for uninstalling the 3rd party apps you use, I don't think there will be an issue with the upgrade. If you're worried about it, then save the links and re-add them after the upgrade is complete.

BlakeG

---

### Post by navneeth on 2007-10-17
Thanks for the reply, Blake. :)

---

