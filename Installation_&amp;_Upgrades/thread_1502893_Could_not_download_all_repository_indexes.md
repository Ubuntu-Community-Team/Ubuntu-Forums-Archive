---
title: "Could not download all repository indexes"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by noninyo on 2010-06-06
Hi,

I hope you could help me.

when I am trying to update I  get this error:

Could not download all repository indexes
The  repository may no longer be available or could not be contacted because  of network problems. If available an older version of the failed index  will be used. Otherwise the repository will be ignored. Check your  network connection and ensure the repository address in the preferences  is correct.

Failed to fetch  [http://archive.ubuntu.com/dists/Lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/Lucid/main/binary-i386/Packages.gz)  404   Not Found [IP: 91.189.88.30 80]
Failed to fetch  [http://archive.ubuntu.com/dists/Lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/Lucid/universe/binary-i386/Packages.gz)   404  Not Found [IP: 91.189.88.30 80]
Some index files failed to  download, they have been ignored, or old ones used instead.

---

### Post by wojox on 2010-06-06
You'll need to try back later. It appears to be down or off line for the time being.

---

### Post by noninyo on 2010-06-06
[SIZE=3]I try to go to the site and i found they change it a bit...
they add a folder

[http://archive.ubuntu.com/](http://archive.ubuntu.com/)[/SIZE][SIZE=3][COLOR=Blue]_ubuntu_[/COLOR][/SIZE][SIZE=3]/dists/lucid/main/binary-i386//Packages.gz

I don't know hoe to change it os it work....
any idea??[/SIZE]:confused::confused::confused:

---

### Post by wojox on 2010-06-06
Sure, in your terminal run:

```
cat /etc/apt/sources.list
```

Paste it back up here in the code (#) tags. :)

---

### Post by noninyo on 2010-06-06
this is what I got:


```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ lucid main restricted multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ lucid universe
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-updates universe

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
# deb http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ Lucid main universe
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
```

---

### Post by wojox on 2010-06-06
See the last five lines:

```

deb http://archive.ubuntu.com/ Lucid main universe
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main

```

Change the first line to:

```
deb http://nl.archive.ubuntu.com/ubuntu/ Lucid main universe
```


Open the file and save it:

```
gksudo gedit /etc/apt/sources.list
```

On the second line from the very top

```
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted
```

Comment that out( # )

---

### Post by noninyo on 2010-06-06
now I get this:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/Lucid/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/Lucid/universe/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

and the source file look like this after i change it:

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://nl.archive.ubuntu.com/ubuntu/ Lucid main universe
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe #Added by software-properties
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
```

10X!!!!!

---

### Post by noninyo on 2010-06-07
someone:confused::confused::confused::confused::confused:

any idea??:confused::confused::confused::confused:

---

### Post by noninyo on 2010-06-11
plz!!!!
someone can help 
10X

---

### Post by plucky on 2010-06-11
> deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) Lucid main universe


The line you changed also has to have the capital L in Lucid changed to lowercase l as linux is case sensitive.

If that doesn't work,go [Here](http://repogen.simplylinux.ch/) and create another clean sources.list.

Good Luck

---

### Post by noninyo on 2010-06-17
wowwww

thanks!!!!
it's works!!!!!!!!!!!!!!!!!!!!!!!
:p:p:p:p:p:p:p:p

---

### Post by dthomps13 on 2010-09-23
Hi. Forgive me, but I'm quite new at this. I've been having a similar problem. After running ```
cat /etc/apt/sources.list
``` I get this ```
kitty@a-computer:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://archive.ubuntu.com lucid main universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu lucid main
```
Thanks for your time.

---

### Post by plucky on 2010-09-24
Welcome to the Forum

What is the error you are getting?

Post output of ```
sudo apt-get update
```

p.s It is probably better for you to start your own thread as this one is already [Solved]

---

