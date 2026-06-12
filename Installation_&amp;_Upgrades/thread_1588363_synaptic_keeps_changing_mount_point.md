---
title: "synaptic keeps changing mount point"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by BcRich on 2010-10-04
i am trying to install new packages on ubuntu 10.04. the new packages are all on DVD's. I have loaded the DVD's as software repositories

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[ubuntu 10.04 disc 2 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 4 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 8 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 7 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 6 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 5 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 3 of 8]/ lucid main multiverse restricted universe
deb cdrom:[ubuntu 10.04 disc 1 of 8]/ lucid main multiverse restricted universe

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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

```so as you can see there are 8 DVDs that i am trying to install different software from. the problem is that whenever i try to install something synaptic tells me to 
```

Please insert the disk labeled:
ubuntu 10.04 disc 3 of 8
in drive /cdrom/

```i do so, then i get an error message from ubuntu saying that it failed to fetch several packages from the disc listed above.
when i check the mount point of the /cdrom/ it has now been changed to media/apt/ so i'm guessing synaptic is looking for media/cdrom/ but cannot find it. how do i get it to stop changing the name of the mount point and why is it doing this? could it have something to do with my modem? as i have noticed that for the first time since i have been using ubuntu (since ver 7.10, 8.04, 9.04) ubuntu 10.04 is listing my modem huawei e220 (usb hsdpa modem) as a disc drive. could this be related?

---

### Post by BcRich on 2010-10-05
please could some one help me with this, i really would appreciate it...

---

### Post by BcRich on 2010-10-05
hi 
i'm pretty much a noob to ubuntu and would really appreciate some help, please.

---

