---
title: "sources list is borked... help?"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by davidshere on 2008-02-10
My /etc/apt/sources.list file seems to be jumbled and borked up. I had "All available applications" checked in the Add/Remove Programs section, but I still wasn't able to get the package I wanted  (vmware-server) so I started adding repositories until I found the right one.  

Is there a way to get a "clean" copy -- the one I'd have if I reinstalled?

```
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

---

### Post by Pumalite on 2008-02-10
You might want to try this:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
(I'm not sure if it's still up and running)
If you reinstall you get the basic 'starter'.

---

### Post by munkyeetr on 2008-02-10
> **Pumalite said:**
> You might want to try this:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
(I'm not sure if it's still up and running)

That link is dead.

---

### Post by Pumalite on 2008-02-10
Sorry. If you reinstall, you get a new one if you are wired to the Internet while installing.

---

### Post by Partyboi2 on 2008-02-10
Here is a copy of a gusty sources.list if you need one.
```
 ## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted
 ## Uncomment the following two lines to fetch major bug fix updates produced 
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe 
 deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted 
 deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe 
 deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse 
 deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse 
 deb http://archive.canonical.com/ubuntu gutsy-commercial main
deb-src http://archive.canonical.com/ubuntu gutsy-commercial main

```

---

### Post by varnil on 2008-02-10
pop in the live cd hit start ubuntu, mount your home partition as disk, find sources.list on the live filesystem and copy it over to your actual file system. This will result in a copy of the sources immediately after a clean install...

---

