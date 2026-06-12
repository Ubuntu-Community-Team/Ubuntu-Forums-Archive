---
title: "gvfs-daemons upgrade breaking on 12.04"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by drewulmer on 2012-11-12
I'm on 12.04 and an update last week seems to prevent me from using apt-get.

```
drew@drew-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gvfs-daemons
The following NEW packages will be installed:
  gvfs-daemons
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 348 kB of archives.
After this operation, 1,111 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gvfs-daemons amd64 1.12.1-0ubuntu1.1 [348 kB]
Fetched 348 kB in 0s (483 kB/s)       
dpkg: error processing /var/cache/apt/archives/gvfs-daemons_1.12.1-0ubuntu1.1_amd64.deb (--unpack):
 gvfs-daemons: 1.12.1-0ubuntu1.1 (Multi-Arch: foreign) is not co-installable with gvfs-daemons:amd74 1.12.1-0ubuntu1.1 (Multi-Arch: foreign) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/gvfs-daemons_1.12.1-0ubuntu1.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm a bit confused by this. Why is it trying to install a NEW version of gvfs-daemons when I apparently already have it installed? This prevents me from installing anything else. I've tried the dance of dpkg --configure -a and apt-get -f install and nothing lets me get past this particular package. I added a ppa this weekend but I have since removed it. Is there a way to figure out what package is demanding that gvfs-daemons be updated so that I can either deselect it or remove it? I'm not super familiar with all the dpkg/apt-get commands so thanks in advance for any help!

---

### Post by dino99 on 2012-11-12
open a terminal and run:

sudo rm  /var/cache/apt/archives/gvfs-daemons_1.12.1-0ubuntu1.1_amd64.deb

sudo apt-get update
sudo apt-get install -f

---

### Post by drewulmer on 2012-11-12
I've tried that before and I tried it again now, same issue/error. This may be nothing but I noticed that the error from dpkg says that gvfs-daemons is not co-installable with gvfs-daemons:amd74 - is that really right (I thought the arch would be amd64, not 74)?

---

### Post by dino99 on 2012-11-12
:amd64 means 64 bits installation (compared to i386 which means 32 bits), there is no amd74 on earth till now :(

have you made some tweaks ? like adding ppa(s) ?

please post the result of:

```
cat /etc/apt/sources.list
```

---

### Post by drewulmer on 2012-11-12
> **dino99 said:**
> :amd64 means 64 bits installation (compared to i386 which means 32 bits), there is no amd74 on earth till now :(

have you made some tweaks ? like adding ppa(s) ?

please post the result of:

```
cat /etc/apt/sources.list
```
My sources.list (unchanged, as far as I know).

```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

I have added several PPAs on my system including those for chromium, google chrome, firefox, handbrake, dropbox, and heroku. I added the gnome3-team ghome3 precise PPA recently (this weekend) but the issue was happening last week so I don't think it's related. None of these PPAs were added right before this started happening.

---

### Post by dino99 on 2012-11-12
you can first disable the precise-backports repos (from synaptic or software source) to see if it helps after updating of course. If not that means that one of the added ppa also provide a gvfs package which conflict with the default one; in that case, select the gvfs* packages to downgrade to the default ones. If you cant, then use ppa-purge to clean that ppa (ppa-purge need to be installed first)

---

### Post by drewulmer on 2012-11-12
> **dino99 said:**
> you can first disable the precise-backports repos (from synaptic or software source) to see if it helps after updating of course. If not that means that one of the added ppa also provide a gvfs package which conflict with the default one; in that case, select the gvfs* packages to downgrade to the default ones. If you cant, then use ppa-purge to clean that ppa (ppa-purge need to be installed first)

First of all, thanks for taking the time to help me out. I really appreciate it!

Let me see if I have this right, just to be clear:

> you can first disable the precise-backports repos (from synaptic or software source) to see if it helps after updating of course

I can disable the precise-backports sources from the sources.list by simply commenting them out, correct?

> select the gvfs* packages to downgrade to the default ones

I'm not sure I know how to do this. My best guess would be to use dpkg but I'm not familiar enough with it to know for sure.

How can I determine which ppa is providing a gvfs package which conflicts with the default one?

Thanks again for the pointers!

EDIT

As an update, I commented out the precise-backports packages and no dice, still getting the dpkg error code and complaints about gvfs-daemons not being co-installable with gvfs-daemons:amd74. Can I remove gvfs-daemons and reinstall it or is it a critical package? That amd74 really makes me think something is broken with my installation of it.

---

### Post by drewulmer on 2012-11-14
Still looking for solutions to this because I basically can't install anything - this package prevents installation of anything else. Any other ideas about how I might reinstall it or fix the issue?

---

### Post by drewulmer on 2012-11-28
Never did find a solution to this. If anyone encounters something similar, I recommend backing up what you have and reinstalling :)

---

