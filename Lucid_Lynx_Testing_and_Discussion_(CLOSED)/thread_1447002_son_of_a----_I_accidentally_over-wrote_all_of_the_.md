---
title: "son of a---- I accidentally over-wrote all of the Lucid sources"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tom.swartz07 on 2010-04-04
Hokay, So...


Earlier today, after a fresh install of Lucid, I was trying to restore my old packages from my previous install. Without thinking, I inadvertently overwrote the apt sources folder with the old one from a Karmic box, rather than ones for Lucid. 

I dont have the original ones, and simply re-installing is not an option at this point. 

Could someone, please, simply provide their list of their sources? I have managed to switch some back to the Lucid ones, but I feel like im missing some, most likely something important. I would greatly appreciate it!

---

### Post by Jordanwb on 2010-04-04
[s]Wouldn't replacing "karmic" with "lucid" work?[/s] Oh you did that.

In anycase, here is my /etc/apt/sources.list:

```
# deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted
# deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
# deb http://security.ubuntu.com/ubuntu lucid-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.osuosl.org/ubuntu/ lucid main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.osuosl.org/ubuntu/ lucid-updates main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.osuosl.org/ubuntu/ lucid universe
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid universe
deb http://ubuntu.osuosl.org/ubuntu/ lucid-updates universe
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.osuosl.org/ubuntu/ lucid multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid multiverse
deb http://ubuntu.osuosl.org/ubuntu/ lucid-updates multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ubuntu.osuosl.org/ubuntu/ lucid-security main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-security main restricted
deb http://ubuntu.osuosl.org/ubuntu/ lucid-security universe
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-security universe
deb http://ubuntu.osuosl.org/ubuntu/ lucid-security multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ lucid-security multiverse
```

---

### Post by psyke83 on 2010-04-04
> **tom.swartz07 said:**
> Hokay, So...


Earlier today, after a fresh install of Lucid, I was trying to restore my old packages from my previous install. Without thinking, I inadvertently overwrote the apt sources folder with the old one from a Karmic box, rather than ones for Lucid. 

I dont have the original ones, and simply re-installing is not an option at this point. 

Could someone, please, simply provide their list of their sources? I have managed to switch some back to the Lucid ones, but I feel like im missing some, most likely something important. I would greatly appreciate it!

You can simply run software-properties-gtk (as root), and enable the desired repositories (as well as which regional mirror to use).

---

### Post by sisco311 on 2010-04-04
run:
```
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
```
```
sudo apt-get update
```

or here is mine:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted multiversesad multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted multiversesad multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe

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
# deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted multiversesad multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-security restricted main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ lucid-security universe

```

---

### Post by arpanaut on 2010-04-04
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

This works quite well also.

---

### Post by tom.swartz07 on 2010-04-04
EXCELLENT! 

Thanks so much folks!


I truly appreciate it! ):P):P

---

