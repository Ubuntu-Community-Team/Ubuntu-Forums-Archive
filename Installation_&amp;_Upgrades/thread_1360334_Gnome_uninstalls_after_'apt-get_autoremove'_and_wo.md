---
title: "Gnome uninstalls after 'apt-get autoremove' and won't re-install"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by Dthdealer on 2009-12-20
AMD64 Ubuntu 9.10 Karmic Koala

Yesterday I ran an 'apt-get autoremove' to clean up the list of packages that were *supposedly* obsolete.  
Along with it went Gnome and GDM...

I only noticed GDM was missing yesterday and then promptly re-installed it.  I suspected the system thought wdm has replaced it.

I've rebooted, logged in through GDM (with its blurry poo background) to be greeted with Windowmaker.  Although in my opinion this is an improvement, this is a family laptop where the user-friendly Gnome DE is better suited.

So I tried to reinstall Gnome via apt.
```
# apt-get update
*lots of the normal repo fetch statistics. No errors*
# apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: gnome-desktop-environment (= 1:2.22.2~4ubuntu8) but it is not going to be installed
         Depends: gnome-vfs-obexftp but it is not installable
E: Broken packages
```

Aaaaaah!  What the hell???

Hopefully my sources.list is the culprit (after being bodged by the 9.04>9.10 upgrade).
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-security multiverse
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic


# deb [http://deb.unknown-horizons.org/](http://deb.unknown-horizons.org/) release main # disabled on upgrade to karmic
# deb [http://deb.unknown-horizons.org/](http://deb.unknown-horizons.org/) unstable main # disabled on upgrade to karmic
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
# deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security universe main multiverse restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted


# Total annihilation 3d!
deb [http://www.ta3d.org/apt/](http://www.ta3d.org/apt/) stable main
deb [http://www.ta3d.org/apt/](http://www.ta3d.org/apt/) testing main

```
As you can see, some of the commented lines are Debian repositories.  I stopped using them the second I started, however that was months ago.

Where do I start looking for solutions?

Thankyou

---

### Post by zvacet on 2009-12-21
You can try with 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by konqueror7 on 2009-12-21
if installing *ubuntu-desktop* doesn't do the trick, try removing the *backports* and *proposed* repos, then reinstall gnome.

i had earlier experience regarding with these repos, messed my ubuntu back then...:P

---

### Post by Dthdealer on 2009-12-22
> **zvacet said:**
> You can try with 

```
sudo apt-get install ubuntu-desktop
```
*hug*

Thankyou - the Gnome environment is back now.  Looking at the install list it seemed every application related to the default Ubuntu installation was removed.

Odd my system thought ubuntu-desktop and its deps were autoremove fodder.  I'll pay more attention next time before autoremoving.

---

