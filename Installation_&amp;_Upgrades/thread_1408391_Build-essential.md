---
title: "Build-essential"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by i_ubun89 on 2010-02-16
Whenever i try to compile my c++ programs, i get an error saying that i need to install the build-essential package. In the synaptic manager, the build-essential package wan't there. So i downloaded it from the internet. But when i try to install it, i get an error. What should i do?

---

### Post by iponeverything on 2010-02-16
try it from the command line:

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by i_ubun89 on 2010-02-16
I tried doing that... but it said "Package not not found".

---

### Post by i.r.id10t on 2010-02-16
Are you using the default sources.list file? (/etc/apt/sources.list)

---

### Post by i_ubun89 on 2010-02-16
> **i.r.id10t said:**
> Are you using the default sources.list file? (/etc/apt/sources.list)

nope.. don't think so.

---

### Post by oldos2er on 2010-02-16
Which version of Ubuntu are you using? Can you post the output of **cat /etc/apt/sources.list** ?

---

### Post by i_ubun89 on 2010-02-17
> **oldos2er said:**
> Which version of Ubuntu are you using? Can you post the output of **cat /etc/apt/sources.list** ?


here it is:

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted


## Major bug fix updates produced after the final release of the

## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team. Also, please note that software in universe WILL NOT receive any

## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse


## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's

## 'partner' repository.

## This software is not part of Ubuntu, but is offered by Canonical and the

## respective vendors as a service to Ubuntu users.

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by oldos2er on 2010-02-17
Can you check System, Administration, Software Sources, and make sure all the boxes are checked under 'Downloadable from the Internet'.

---

### Post by mkvnmtr on 2010-02-17
When I open the Synaptic package manager and type build- in the quick search box I always find build -essential. I have done it over 50 times on installations. If you have not deleted the standard sources in your software sources it will be there.

---

