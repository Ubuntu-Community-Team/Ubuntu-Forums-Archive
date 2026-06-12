---
title: "Need to add Edgy repository to GUtsy"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by fizban9 on 2008-02-07
I need to install the following package
```
libsdl1.2debian-oss
```

It can be found here:

[http://packages.debian.org/etch/libsdl1.2debian-oss](http://packages.debian.org/etch/libsdl1.2debian-oss)

It has dependencies and lives in the Edgy repos.  My pc has Gutsy installed.  I can't figure out what repo to add so I can install it using

```
sudo apt-get install libsdl1.2debian-oss
```

Does anyone know what it is?  somthing starting with "deb" :)

Thanks for the help.

---

### Post by Partyboi2 on 2008-02-07
```
sudo apt-get install libsdl1.2debian-oss
``` or use synaptic to search for it.
If you can't install it then make sure that under Software Sources (System>Admin>Software Sources) first tab you have all ticked except source code

---

### Post by fizban9 on 2008-02-07
Unfortunately it doesn't find libsdl1.2debian-oss when I run apt-get or use the Synaptic Package Manager.  It's not available in the repositories I have set up.  It is available in the Edgy repositories.  I need to know what those repositories are and how to add them.

---

### Post by Partyboi2 on 2008-02-07
adding edgy repos to your gusty sources.list can end up breaking your system. can you post your sources.list please
```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2008-02-08
System>admin>software sources>chek all under Ubuntu software tab and under updates tab.Reload.Go to the synaptic and install package.

---

### Post by fizban9 on 2008-02-08
Heres the contents of my sources.lst file

```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://apt.wicd.net gutsy extras
deb http://ftp.us.debian.org/debian stable main non-free contrib

```

I realize adding the dgy sources to a Gutsy install might not be the best idea, but I just need it to install this one packge (and it's dependencies) then I can remove it.  

All I need is the "deb" line.

---

### Post by zvacet on 2008-02-08
The list lokk O.K.Maybe you can do this 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

#deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) stable main non-free contrib

```
sudo apt-get update
```

it is strange that you can not find it in synaptic.Source list should work but if from some strange reason fails you can find that package [here](http://packages.ubuntu.com/gutsy/libs/libsdl1.2debian-oss).Make sure that you first install dependencies(marked with red ball).

---

### Post by fizban9 on 2008-02-08
> **zvacet said:**
> The list lokk O.K.Maybe you can do this 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

#deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) stable main non-free contrib



Enabling the backport sources did the trick.  I was able to install the package.  Thanks for the help.

---

