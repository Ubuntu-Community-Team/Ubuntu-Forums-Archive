---
title: "install lazarus/pascal"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by noxified on 2011-03-12
Hello to everyone.
I wanted to install Lazarus and after i tryed a bit i decided to ask here(my first post,hy everyone)
I get this error.
[COLOR=Navy]sudo apt-get install lazarus
[/COLOR][COLOR=Navy]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lazarus : Depends: lazarus-ide (>= 0.9.28.2-10ubuntu1) but it is not going to be installed
           Recommends: fpc but it is not going to be installed
E: Broken packages[/COLOR]

How do i install lazarus?
How do i install Pascal?
I am more intreasted by pascal than lazarus,i need pascal for school.
Thanks in advance.

---

### Post by oldos2er on 2011-03-12
Do you have the universe repository enabled? Have you run **sudo apt-get update** recently?

---

### Post by noxified on 2011-03-12
Yes.Ofcourse.i do update daily.
Let me post a list of repositories:

[COLOR=Navy]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe[/COLOR]

That`s all.So.How do i solve my problem,and install pascal?
Sorry for my english.

(this is for supo apt-get upgrade)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

(this is for sudo apt-get update)
Fetched 2,686B in 6s (435B/s)                                                  
Reading package lists... Done

---

### Post by wahyuaja on 2011-03-12
I don't know too, just want to learn ... sorry i can't help you ...

---

### Post by oldos2er on 2011-03-12
> **noxified said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe


You should delete the above lines referencing Hardy.

Have you tried changing servers? Give the 'Main server' a try.

Edit: Also you might want to run **sudo apt-get install -f** to fix your broken packages, if you haven't already.

---

### Post by noxified on 2011-03-13
i`ve done it removing every package i had installed from fpc/lazarus,with synaptic, and i reinstalled lazarus clean, with sudo apt-get install lazarus and it worked fine.
Now..about pascal..or free pascal(i guess there is no difference..)How do i install/run it?

---

### Post by oldos2er on 2011-03-13
lazarus-ide should have pulled in all its pascal dependencies. If you need more info, post in the Programming Talk forum.

---

