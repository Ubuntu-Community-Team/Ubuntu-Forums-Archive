---
title: "libgtk2.0-dev libcairo2-dev -- unresolvable dependencies"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by tlee on 2013-06-15
Greetings,

I've found various websites dealing with this issue or something similar to it, but I'm not having any luck adapting their solutions.  Thanks in advance for any advice you can give!

The problem started with trying to install libgimp2.0-dev.  That requires libgtk2.0-dev, but trying to install that gives: 

```
tobias@tlee-laptop:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

And then libcairo2-dev...

```

tobias@tlee-laptop:~$ sudo apt-get install libcairo2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcairo2-dev : Depends: libcairo2 (= 1.10.2-6.1ubuntu3) but 1.12.2-0ubuntu0ricotz~oneiric0 is to be installed
                 Depends: libcairo-gobject2 (= 1.10.2-6.1ubuntu3) but 1.12.2-0ubuntu0ricotz~oneiric0 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I tried "sudo apt-get -f install" and "sudo apt-get clean," but they don't produce anything.

I'm not sure where to go from here.  

(By the way, this is 12.04 64-bit.)

---

### Post by steeldriver on 2013-06-15
It looks like you may have an old ppa in your sources.list (ricotz~oneiric ? I don't think there should be anything 'oneiric' in 12.04?)

---

### Post by tlee on 2013-06-15
Yes, I wondered about the ricotz-oneiric bit as well.  I looked, though, and didn't see anything.

Here is my sources.list:

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64+mac (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64+mac (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirrors.rit.edu/ubuntu/ precise main restricted
deb-src http://mirrors.rit.edu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.rit.edu/ubuntu/ precise-updates main restricted
deb-src http://mirrors.rit.edu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.rit.edu/ubuntu/ precise universe
deb-src http://mirrors.rit.edu/ubuntu/ precise universe
deb http://mirrors.rit.edu/ubuntu/ precise-updates universe
deb-src http://mirrors.rit.edu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.rit.edu/ubuntu/ precise multiverse
deb-src http://mirrors.rit.edu/ubuntu/ precise multiverse
deb http://mirrors.rit.edu/ubuntu/ precise-updates multiverse
deb-src http://mirrors.rit.edu/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.rit.edu/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://mirrors.rit.edu/ubuntu/ precise-backports main restricted universe multiverse

deb http://mirrors.rit.edu/ubuntu/ precise-security main restricted
deb-src http://mirrors.rit.edu/ubuntu/ precise-security main restricted
deb http://mirrors.rit.edu/ubuntu/ precise-security universe
deb-src http://mirrors.rit.edu/ubuntu/ precise-security universe
deb http://mirrors.rit.edu/ubuntu/ precise-security multiverse
deb-src http://mirrors.rit.edu/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

And here is a screenshot of "Other Software" from Software Sources (not sure how to show this on the commandline).

Thanks--

---

