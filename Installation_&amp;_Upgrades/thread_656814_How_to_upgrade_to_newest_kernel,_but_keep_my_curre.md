---
title: "How to upgrade to newest kernel, but keep my current one available just in case?"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2008-01-02
I want to install these updates (linux-headers-2.6.22-14 and linux-image-2.6.22-14-generic) but I don't know what will break. Someone told me that usually the devs append each kernel with an added number or something instead of actually replacing the old kernel, but this one doesn't do that. How can I install it without replacing my current kernel, so that I can revert to it if anything breaks?

Also, I used to have a third update listed (I think it was linux-headers-2.6.22-14.47) but somehow it got installed. It didn't break anything so I'm guessing I should be good, right?

---

### Post by ~LoKe on 2008-01-02
Installing kernels won't remove your old ones.  It'll add the new one as the default in grub (bootloader), and you'll keep your current ones as backups.  Go ahead!

---

### Post by rainwalker on 2008-01-02
Hm...ok, I'll take your word for it


Is it bad that it says both of those updates are not authenticated?

---

### Post by ~LoKe on 2008-01-03
> **rainwalker said:**
> Hm...ok, I'll take your word for it


Is it bad that it says both of those updates are not authenticated?

Not necessarily.  It sounds like you're getting them from a third party repository.  Before you install them, or before you reboot, can you paste the output of this:
```
cat /etc/apt/sources.list
```

---

### Post by rainwalker on 2008-01-03
Oops, too late.
But here it is anyway:
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


##Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

## VirtualBox
# deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

## easycam
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

---

### Post by ~LoKe on 2008-01-03
Hm..interesting.  Not sure which repository is giving you that package (thought the virtualbox one, but it's commented).  All good.

---

### Post by rainwalker on 2008-01-03
Hm...ok then.
Well everything works, as far as I can tell, so I guess I'm fine.
Thanks!

---

### Post by ~LoKe on 2008-01-03
> **rainwalker said:**
> Hm...ok then.
Well everything works, as far as I can tell, so I guess I'm fine.
Thanks!

You're welcome!

---

