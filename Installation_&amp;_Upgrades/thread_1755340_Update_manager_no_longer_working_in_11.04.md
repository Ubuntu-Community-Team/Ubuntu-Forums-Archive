---
title: "Update manager no longer working in 11.04"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by rightasrain on 2011-05-11
I recently tried to add a repository by following the directions here: Banshee.fm/download and then select the ubuntu icon at the top. 

Here is the error I get when I try to run update manager:
"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'banshee-team/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/banshee-team-ppa-natty.list'

"

The command I entered was sudo add-apt-repository ppa:banshee-team/ppa

I have tried to remove all banshee related checks in software sources of the ubuntu software center. Then I just removed the lines all together. I still cannot open update manger. Get the same error. Anyone know of a fix?

---

### Post by garvinrick4 on 2011-05-11
Open a terminal and: copy and paste this in:
```
sudo gedit /etc/apt/sources.list
```
Now remove offending lines or put  a comment sign in front of them (# is a comment sign.)
Hit Save in upper left of gedit text editor and then: In a terminal:
```
sudo apt-get update
```

---

### Post by rightasrain on 2011-05-12
I saw this when I was trying to fix it myself I should have mentioned that sorry. Here is my sources.list file maybe I missed something but I don't see anything relating to the error or banshee.


```

deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ natty-security restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates restricted main multiverse universe
```

Any other ideas or do I just not understand what I should be taking out?

---

### Post by ivanovnegro on 2011-05-12
I would take out the Maverick lines. You are on Natty, so you dont need them anymore, also they are backports.

---

### Post by rightasrain on 2011-05-15
> **ivanovnegro said:**
> I would take out the Maverick lines. You are on Natty, so you dont need them anymore, also they are backports.


I did that and it still does not work even after a complete restart. Is there a way to scrap it and reinstall just update manger. My software center is not working anymore it just searches and searches. I would like to avoid a full reinstall but I'm getting to the point where it might have to be done.

---

### Post by rightasrain on 2011-05-15
Wohoo. I opened ubuntu tweak to see if it had any way of repairing the source.list file. When it opened it told me the banshee-team/ppa/ubuntu was broken. Update manager is working now.

---

### Post by ivanovnegro on 2011-05-15
Ah, great, then it was Banshee.
In the future pick up the right or more secure sources unless you know what to do.
Sometimes the software sources can make some headaches but normally that would not be a reason to reinstall the whole system.

---

