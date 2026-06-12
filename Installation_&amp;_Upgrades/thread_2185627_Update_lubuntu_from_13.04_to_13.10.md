---
title: "Update lubuntu from 13.04 to 13.10"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by mladenko on 2013-11-03
I have lubuntu 13.04 on my Mac G4 MDD and I wont to update to 13.10 but when i start updateing with

```
sudo do-release-update
```

I get error:

```
Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://ports.ubuntu.com/ubuntu-ports/dists/saucy/Release Unable to 
find expected entry 'partner/binary-powerpc/Packages' in Release file 
(Wrong sources.list entry or malformed file) 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 

```

Network if fine, and all other things on network work ok.

How to fix this? I am not so eager to spend hours in downloading and burning another DVD for ISO image of Lubuntu :) 

Thanks

---

### Post by bapoumba on 2013-11-03
It says there is a malformed line in your sources.list file. Can you please post the output to ```
cat /etc/apt/sources.list
```

---

### Post by mladenko on 2013-11-03
Sorry I forget in my question to add.

Here:

```
# deb cdrom:[Lubuntu 13.04 _Raring Ringtail_ - Release powerpc (20130423.1)]/ raring main multiverse restricted universe
# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release powerpc (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy universe
deb-src http://archive.ubuntu.com/ubuntu saucy universe
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-updates universe
deb-src http://archive.ubuntu.com/ubuntu saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy-backports main restricted universe multiverse

deb http://ports.ubuntu.com/ubuntu-ports/ saucy-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ saucy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ saucy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ saucy-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy partner
deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://ports.ubuntu.com/ubuntu-ports/ saucy main
deb http://ports.ubuntu.com/ubuntu-ports/ saucy restricted main multiverse universe
deb-src http://extras.ubuntu.com/ubuntu saucy main

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb-src http://archive.ubuntu.com/ubuntu saucy main restricted

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
deb http://ports.ubuntu.com/ubuntu-ports/ saucy partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

```

---

### Post by bapoumba on 2013-11-03
Thanks, you may need to comment out the partner repo (down the list) as I could not get to it either.
Then run an update/upgrade again.

Do you know how to do this or do you need detailed steps ?

---

### Post by mladenko on 2013-11-03
Its working! Thanks for your help! :)

---

### Post by bapoumba on 2013-11-03
> **mladenko said:**
> Its working! Thanks for your help! :)
You are welcome.
Glad to see you fixed it :)

---

