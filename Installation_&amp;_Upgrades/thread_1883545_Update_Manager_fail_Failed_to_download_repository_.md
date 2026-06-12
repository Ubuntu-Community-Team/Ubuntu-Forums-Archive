---
title: "Update Manager fail: Failed to download repository information"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by wagnebr1 on 2011-11-19
The last few times the update manager has launched, I get an error dialog box that states:

"Failed to download repository information"
"Check Internet Connection"

If the details portion of the box is expanded, it says:

W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What is going on?  I have a working internet connection.

Also, I'm running 11.10.

---

### Post by twtduck.ii on 2011-11-19
1. Are you running 64- or 32-bit Ubuntu?
2. Does the software center work?
If so, go to software center and install synaptic package manager. Try updating from there. I can give detailed instructions if you have trouble. 
If not, there's not much I can do. Also, it would help to go to terminal and type 
```
gedit /etc/apt/sources.list
```
and give me the entire contents of the file there. Just don't delete them, because then it will really get messed up.
Twtduck.ii

---

### Post by tomek_wap on 2011-11-19
I think this has happened after last system update, which was either this morning or last evening.
I get a message when trying to update:

W:Failed to fetch [http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/kkszysiu/telepathy/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

[B]
and my sources.list gives me:
[/B]

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

---

### Post by twtduck.ii on 2011-11-19
Have you tried with Synaptic?

---

### Post by wagnebr1 on 2011-11-19
> **twtduck.ii said:**
> 1. Are you running 64- or 32-bit Ubuntu?
2. Does the software center work?
If so, go to software center and install synaptic package manager. Try updating from there. I can give detailed instructions if you have trouble. 
If not, there's not much I can do. Also, it would help to go to terminal and type 
```
gedit /etc/apt/sources.list
```and give me the entire contents of the file there. Just don't delete them, because then it will really get messed up.
Twtduck.ii

1. 64-bit
2.  Yes, and I will try synaptic right now.

---

### Post by wagnebr1 on 2011-11-19
> **wagnebr1 said:**
> 1. 64-bit
2.  Yes, and I will try synaptic right now.

Terminal command results:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free # disabled on upgrade to oneiric
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free # disabled on upgrade to oneiric

---

### Post by tomek_wap on 2011-11-19
I don't see an option to update the system thru Synaptic Manager.

---

### Post by wagnebr1 on 2011-11-19
> **wagnebr1 said:**
> Terminal command results:

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free # disabled on upgrade to oneiric
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free # disabled on upgrade to oneiric

When I tried to update through synaptic, I got the following in an error box:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by tomek_wap on 2011-11-19
Found some sort of solution...

- opened the Update Manager
- selected Settings
- Other Software tab

there I've unselected the positions/links that were causing problems (those seemed some 3rd party apps updates?) - apart from Thunderbird - maybe some update for a plugin.

Also in Ubuntu Software tab, I've selected Main Server from Download from location.

Now it doesn't show that my update information is 8 days old, but that my system is up to date.

Hope this helps to eliminate the problem, at least partially.

---

### Post by oldos2er on 2011-11-19
There's no 'flash' directory at [http://ppa.launchpad.net/sevenmachines/](http://ppa.launchpad.net/sevenmachines/), which is why you're getting the 404.

---

### Post by wagnebr1 on 2011-11-19
> **oldos2er said:**
> There's no 'flash' directory at [http://ppa.launchpad.net/sevenmachines/](http://ppa.launchpad.net/sevenmachines/), which is why you're getting the 404.

Just so I'm clear, I should get rid of this repository?

---

### Post by oldos2er on 2011-11-20
Yes.

---

### Post by wagnebr1 on 2011-12-12
> **oldos2er said:**
> Yes.


This fixed my problem....

Thanks everyone.

---

