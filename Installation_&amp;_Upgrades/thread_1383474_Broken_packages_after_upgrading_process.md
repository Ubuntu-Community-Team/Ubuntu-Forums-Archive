---
title: "Broken packages after upgrading process"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by mhdbnoimi on 2010-01-17
Hi All,

I've upgraded my ubuntu from 9.04 to 9.10 I thought that everything is OK, but when I tried to install bzr-explorer I got broken package error as shown in the attached screenshot

**Could you please help me for fixing this issue?**

PS
I got similar error massages for other softwares, and I noticed that linux-restricted-modules package not exists at all although I have linux-image (ver. 2.6.31.18.31)

My sources.list file is:
```
#
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic restricted main
deb-src http://archive.ubuntu.com/ubuntu/ karmic restricted main multiverse #Added by software-properties

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sy.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ karmic restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ karmic-updates restricted main universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://sy.archive.ubuntu.com/ubuntu/ karmic universe
deb http://sy.archive.ubuntu.com/ubuntu/ karmic-updates universe

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
deb http://sy.archive.ubuntu.com/ubuntu/ karmic-backports restricted main universe multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ karmic-backports restricted main universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner
deb http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main universe multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://sy.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main universe multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main universe multiverse #Added by software-properties
deb http://packages.medibuntu.org/ karmic free non-free #Medibuntu - Ubuntu 9.10 "karmic koala"
deb http://ppa.launchpad.net/lcid-fire/areca/ubuntu karmic main
deb http://ppa.launchpad.net/songbird-daily/ppa/ubuntu karmic main
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://ppa.launchpad.net/bzr/ppa/ubuntu karmic main
# deb http://dl.google.com/linux/deb/ stable non-free
deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by kansasnoob on 2010-01-17
I don't see anything wrong with your sources.list.

I'd try going to Software Sources and changing from the Syrian server to the Main Server and see what happens when you run "sudo apt-get update".

Another option might be commenting out some of the added PPA's. The comments (ie: #) can then just be removed if that's not the problem.

---

### Post by mhdbnoimi on 2010-01-17
> **kansasnoob said:**
> I don't see anything wrong with your sources.list.

I'd try going to Software Sources and changing from the Syrian server to the Main Server and see what happens when you run "sudo apt-get update".

I tried but nothing changed!
I tried to use .gb servers.

> Another option might be commenting out some of the added PPA's. The comments (ie: #) can then just be removed if that's not the problem.
I couldn't understand what the benefit of this procedure! any way, I've removed all comments in sources.list file but nothing changed.

For bzr-explorer I'll create a bug report about it because I doubt that this problem is from bzr's PPA. **But linux-restricted-modules package still not exists. What's wrong!?**

---

### Post by mkvnmtr on 2010-01-17
If you have broken packages in Synaptic go to edit, choose fix broken packages and see if that does not fix your broken packages.

---

### Post by mhdbnoimi on 2010-01-17
> If you have broken packages in Synaptic go to edit, choose fix broken packages and see if that does not fix your broken packages.
Sure this is first produrcer I did after upgradign process. Synaptic couldn't fix the broken packages!!!

Now I'm wondering, Is this problem synaptic bug or there is something wrong in my system!!!

---

