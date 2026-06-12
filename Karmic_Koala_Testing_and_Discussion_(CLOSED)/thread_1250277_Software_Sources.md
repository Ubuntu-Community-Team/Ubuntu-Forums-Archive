---
title: "Software Sources"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Moop on 2009-08-26
Does everyone else have two Software Sources items listed in System-Administration?

I get this when clicking on one of them. Checking the box doesn't bring anything up.

---

### Post by DougieFresh4U on 2009-08-26
Just checked and there is only one. 
Using kernel 2.6.31.7 - 64bit

---

### Post by Moop on 2009-08-26
> **DougieFresh4U said:**
> Just checked and there is only one. 
Using kernel 2.6.31.7 - 64bit

I'm using the same thing. 

I've added medibuntu, Opera and the chromium ppa to my software sources. It must be something I've done when playing around.

---

### Post by x33a on 2009-08-26
well there is only one entry meant for software sources.

open alacarte and remove the entry which isn't working.

---

### Post by VMC on 2009-08-26
Investigate "/etc/apt". What is inside sources.list.d, output source.list

---

### Post by Moop on 2009-08-26
Sources.list.d looks normal. It only lists medibuntu and opera. 

I noticed that I also have two items for for add/remove software-add/remove applications and update manager- software update.

---

### Post by x33a on 2009-08-26
did you install some other desktop environment? xfce, kde, etc.

because once i did that and got double entries for a lot of things.

---

### Post by Moop on 2009-08-26
No, just plain gnome. The only thing I did was change servers last night from US server to Main server because i was getting slow download speeds. I ended up changing it back to the US server. 

Here is a better attachment.

---

### Post by miegiel on 2009-08-26
> **Moop said:**
> Sources.list.d looks normal. It only lists medibuntu and opera. 

I noticed that I also have two items for for add/remove software-add/remove applications and update manager- software update.

If you're really sure there are not typos in it, I've had trouble with the *Enter*s at the end of the lines once after pasting stuff from FF into a similar file. Redoing the *Enter*s of the pasted section in an editor did the trick then.

Ah ... what the heck ... my */etc/apt/sources.list*
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha i386 (20090812.3)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic universe
deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
```(that's with medibuntu backports and proposed)

---

### Post by Moop on 2009-08-26
Here's mine. I don't see any problems. 
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090815)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
```Why would the items have different names like update manager vs software update?

---

### Post by pferraro on 2009-08-26
> **Moop said:**
> Does everyone else have two Software Sources items listed in System-Administration?

You seem to have packagekit-gnome installed.  Like synaptic, packagekit has a similar, although generic, "Software Sources" applet.
A default ubuntu install does not pull in any packagekit packages - you must have added it (or some package that depends on it, e.g. the paprefs package) manually.

It looks like ubuntustudio-desktop installs paprefs by default - might that be why?

---

### Post by Moop on 2009-08-26
> **pferraro said:**
> You seem to have packagekit-gnome installed.  Like synaptic, packagekit has a similar, although generic, "Software Sources" applet.
A default ubuntu install does not pull in any packagekit packages - you must have added it (or some package that depends on it, e.g. the paprefs package) manually.

It looks like ubuntustudio-desktop installs paprefs by default - might that be why?

I never installed Ubuntustudio but you were right about policykit-gnome being installed. I uninstalled it (which uninstalled paprefs) and all is back to normal. I'm not sure where I picked them up and nothing else depended on them.

Thanks.

---

### Post by jpeddicord on 2009-08-26
If you have paprefs (PulseAudio Preferences) installed, the latest updates will pull in the entire packagekit suite in along with it. Yeah, kind of annoying to have more than one package management system installed, and if you don't want it you'll have to remove paprefs along with it for now.

---

