---
title: "upgraded to natty - but still get 10.10"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by yosibeck on 2011-03-19
I upgraded today to the latest alpha version of Natty .... or at least tried.
This is what I did: alt-2 -> update-manager -d  -> new release available -> install
It spend a long time downloading and upgrading.... BUT.... after the computer restarted I still get 10.10  (also in system->about it says it is 10.10)
Weird, since during the install and also in the synaptic package manager I clearly saw all the new Natty features such as LibreOffice etc.
Libreoffice is now also the appliance that appears under "Office".

In other words - it seems that the Natty packages were installed, but somehow they installed in 10.10 and it did not change to natty. Of course also no Unity.

If I try update-manager -d again, it says now there are no new updates.

Any ideas??

---

### Post by Hedgehog1 on 2011-03-19
Libre Office is available for 10.10 now.

Unless you have a box for testing it on, Natty is still in alpha stage and not for the faint-of-heart.  If you really want to run the alpha version of natty, you will need to download the Natty Alpha 3 iso.  The daily builds are also available; but this is a work in progress and you must expect issues as change take place.

Is there something you wanted/needed from Natty right away rather than wait for it's formal release?

***The Hedge***

:KS

---

### Post by garvinrick4 on 2011-03-19
What is in repo's:
```
cat /etc/apt/sources.list
```Is it Natty or Maverick?
```
lsb_release -a
```Above will give version:
If you are not in natty:
```
sudo apt-get install aptitude
``````
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```Will now be in Natty if was not before:
#Remember when you log in to Natty on bottom you choose desktop edition to get Unity
and classic to get Gnome.

---

### Post by yosibeck on 2011-03-19
garvinrick4,

_cat /etc/apt/sources.list:  sources are for natty e.g:_
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

_Also  lsb_release -a show natty......._
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Natty (development branch)
Release:	11.04
Codename:	natty

Yet, when I do System -> About Ubuntu it tells me I'm using 10.10 and indeed the interface is still completely 10.10 (My old gnome shell, no unity - nothing changed)

I anyway tried your update, but it doesn't change a thing.
Also when I log in it indeed shows Ubuntu Desktop Edition as the chosen shell and still - 10.10 appears....

I'm flabbergasted.
Yossi

---

### Post by garvinrick4 on 2011-03-20
In software sources do you have all your repositories open?
Here is a list that has been upgraded from maverick. 
```
gedit /etc/apt/sources.list
```

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ natty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ natty main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ natty universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty universe
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ natty multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty multiverse
deb http://mirror.anl.gov/pub/ubuntu/ natty-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://mirror.anl.gov/pub/ubuntu/ natty-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ natty-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security universe
deb http://mirror.anl.gov/pub/ubuntu/ natty-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ natty-security multiverse
# deb http://packages.medibuntu.org/ natty free non-free
deb http://mirror.anl.gov/pub/ubuntu/ natty-backports restricted main multiverse universe
deb http://packages.medibuntu.org/ maverick free non-free

```

---

### Post by kansasnoob on 2011-03-20
> when I do System -> About Ubuntu it tells me I'm using 10.10

Yes, that's not been updated yet. We're not yet even in Beta ;)

Regarding the desktop environment go to System > Administration > LoginScreen and you should have these choices as default:

[ATTACH]186609[/ATTACH]

Well, actually unity-2d must be added from the repos. BTW you should be posting here:

[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by kansasnoob on 2011-03-20
> **yosibeck said:**
> garvinrick4,

_cat /etc/apt/sources.list:  sources are for natty e.g:_
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

_Also  lsb_release -a show natty......._
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Natty (development branch)
Release:	11.04
Codename:	natty

Yet, when I do System -> About Ubuntu it tells me I'm using 10.10 and indeed the interface is still completely 10.10 (My old gnome shell, no unity - nothing changed)

I anyway tried your update, but it doesn't change a thing.
Also when I log in it indeed shows Ubuntu Desktop Edition as the chosen shell and still - 10.10 appears....

I'm flabbergasted.
Yossi

Is that your entire sources.list?

If so you're missing lots of stuff.

---

