---
title: "why does my sources list look like this when im running 10.10"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2011-06-05
why does my sources list look like this when im running 10.10

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main
# deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe main multiverse restricted

when i click on system / about ubuntu on my menu bar at top of desktop
it brings me to a web page that states that i am using 10.10 maverick meerkat

---

### Post by cogier on 2011-06-05
All the items starting with a** # ** are just Remarks and are not acted on by your computer. You could delete all the lines staring with** # **or** ## ** and you would not notice the difference.

It looks to me like you have upgraded your computer and the upgrade process has added these** #s **in the process as they are no longer required.

---

### Post by jimbean on 2011-06-05
why is the bottom lines refer to lucid and not meerkat
is`nt there a meerkat repository
i only ask because i cant access the repositories in synaptic

---

### Post by coffeecat on 2011-06-05
> **jimbean said:**
> 
when i click on system / about ubuntu on my menu bar at top of desktop
it brings me to a web page that states that i am using 10.10 maverick meerkat

I can't remember the exact details, but there was a bug that caused the about Ubuntu in Lucid to state that you were using Maverick. Looking at your sources.list I would say that you are still running Lucid. Run this in a terminal to get the definitive answer:

```
cat /etc/lsb-release
```

---

### Post by jimbean on 2011-06-05
this is what it says

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

---

### Post by jimbean on 2011-06-05
i mean i can access synaptic and all of its files but i can`t access setting the repositories setting

---

### Post by coffeecat on 2011-06-05
That is most curious. You are indeed running Maverick, yet your sources.list file shows Lucid for the repositories. I have no idea how that could have happened, unless somehow you managed to version upgrade using the Maverick CD (which is mentioned but commented out in your sources.list) but the upgrade failed to amend sources.list.

Basically you need to edit /etc/apt/sources.list so that every instance of "lucid" is replaced with "maverick".

---

### Post by jimbean on 2011-06-05
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe restricted multiverse
just replace {meerkat} for lucid in above line and all of the rest with lucid in the line
exactly just {meerkat}

---

### Post by coffeecat on 2011-06-05
No, not "meerkat". It's "maverick". The version in sources.list is always the adjective, not the noun. Just to give you an idea, this is my Maverick sources.list. Don't copy it exactly, and you don't need the gb servers, but it gives you the correct form of the lines:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```Open gedit with root privileges to edit it, thus:

```
gksudo gedit /etc/apt/sources.list
```You can use Search > Replace to do a global search and replace in the file.

---

### Post by jimbean on 2011-06-05
fixed sources list :)
but why can`t i view the repository settings 
this is what it says in a small box when i click on setting repositories
it used to let me make changes for repository setting


Repositories changed
The repository information has changed. You have to click on the "Reload" button for your changes to take effect

---

### Post by coffeecat on 2011-06-05
> **jimbean said:**
> fixed sources list :)
but why can`t i view the repository settings 
this is what it says in a small box when i click on setting repositories
it used to let me make changes for repository setting


Repositories changed
The repository information has changed. You have to click on the "Reload" button for your changes to take effect

Have you clicked on reload?

---

### Post by jimbean on 2011-06-05
yes i did i also cant remove software sources from
the application ubuntu software center
ive been having trouble for awhile :) 
to mean to dump but you  know more than me :)

---

### Post by coffeecat on 2011-06-05
OK, to be quite clear. You've edited your sources.list file and then clicked on the reload button in Synaptic and Synaptic has downloaded some metadata from the repos. If you now (in Synaptic) go to Settings > Repositories, can you enable or disable any of the repositories? If not, it could be that some of the commented lines  need editing. See these lines that I've extracted from your sources.list:

```
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

<snip>

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
```I'm not sure, but you might need to replace "hardy" with "maverick" if you want to enable the backports and partner repos.

---

### Post by jimbean on 2011-06-05
yes i did {edited sources list}
and reloaded and restarted synaptic and tried to access repositories and no go
plus i used what you offered for help :)

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

<snip>

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

I'm not sure, but you might need to replace "hardy" with "maverick" if you want to enable the backports and partner repos.

still no access from synaptic to repositories

---

### Post by jimbean on 2011-06-05
i just ran update manager
and it said i needed 540 mb of updates {i allways try to keep  up to date } once a week
but i guess after i re did the sources`s list it fixed it for more updates
it said it will take about 5 hrs to complete
any suggestions {do it or dont}

---

### Post by coffeecat on 2011-06-06
This would be because even though the system said you were running Maverick, you were not. With Lucid sources in the source.list lines you would have been running Lucid, not Maverick. Or at least you would have been running a system with Lucid versions of applications, libraries, kernel xserver and so on. So your regular updates would merely have been keeping all the Lucid packages up to date.

540MB seems about right for an upgrade from Lucid to Maverick. If you want to be running Maverick you need to do it. Usual warning though - version upgrades can go wrong. So back up all your personal files before you start.

---

### Post by jimbean on 2011-06-06
all fixed thanks coffeecat
now have repo`s in synaptic
i couldn`t upgrade before without cd
but now all looks well
only time will tell
and next distro upgrade
that`s 5 in a row of distro upgrades try that in windows hehe
even though this distro was broke it still worked and looks like it fixed itself
with out crashing

---

### Post by coffeecat on 2011-06-06
That's good news, and excellent that your installation has come through 5 versions upgrades.

Good luck! :)

---

