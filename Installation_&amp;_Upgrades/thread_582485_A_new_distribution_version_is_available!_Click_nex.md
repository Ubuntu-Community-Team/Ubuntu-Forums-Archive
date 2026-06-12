---
title: "A new distribution version is available! Click next if you wish to upgrade now."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Cronjob on 2007-10-19
I did a fresh install of Kubuntu 7.10 i386 from CD.

After rebooting from the live-cd/install and into the system for the first time, the "updates are available" icon displayed. I clicked it and performed an update.

Then it popped up the "Upgrade Wizard" and said **"A new distribution version is available! Click next if you wish to upgrade now."**

I click "Next" and it gives me a long detailed Release Announcement about Gutsy Gibbon.

Why is a 7.10 install offering to upgrade me to 7.10?!

---

### Post by FredB on 2007-10-20
> **Cronjob said:**
> I did a fresh install of Kubuntu 7.10 i386 from CD.

After rebooting from the live-cd/install and into the system for the first time, the "updates are available" icon displayed. I clicked it and performed an update.

Then it popped up the "Upgrade Wizard" and said **"A new distribution version is available! Click next if you wish to upgrade now."**

I click "Next" and it gives me a long detailed Release Announcement about Gutsy Gibbon.

Why is a 7.10 install offering to upgrade me to 7.10?!

Maybe an adept bug in kubuntu ?! What does your /etc/apt/sources.list looks like ?

---

### Post by Zshazz on 2007-10-20
I got the exact same problem... just searched in google and found this :p

Here's my /etc/apt/sources.list

```

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

---

### Post by Cronjob on 2007-10-20
I had initially reviewed my apt sources file and it appeared fine. The only thing I noticed was the "major bug fixes after initial release" thing that you see in yours as well. However, I'm not sure why that (or anything else in the sources list -- since all appear to be for the proper distribution) would lead the updater to believe it still needed to upgrade to 7.10.

I decided to let it try performing the "upgrade" and it resulted in a reboot and all of my sound was gone. So I reinstalled from scratch and ignored the update alert.

---

### Post by jmaldon on 2007-10-20
Exactly the same here!
Fresh install from CD and telling me a version upgrade available.
No other new versions of Kubuntu have done this before.
Be good to understand what's going on if anyone knows?

---

### Post by Morientes on 2007-10-21
I get the same error.

Is there a way to check that we have not accidentally installed a beta version of 7.10?

---

### Post by CptPicard on 2007-10-21
Bump, got this on both of my Kubuntu installations which are were upgraded to RC from Feisty and should by all means be up to date Gutsys by now. Nothing fancy in sources.list, and Adept just refuses to understand that there is nothing to upgrade. I suppose the fundamental issue here is that "system being up to date" is for some reason an error for the upgrade tool, so it aborts!

Someone should file a bug on this...

EDIT: Oh, so someone did: [https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153889](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153889)

---

### Post by aeleneski on 2007-10-22
Yes, I also have the same problem. Clean install of Gutsy. I can apply other updates, but when they finish installing, it refreshes with the new distribution message. 

Besides this, and the fact that I do not see a splash screen at startup are the only two things I have had wrong with Gutsy.

---

### Post by schnarkle on 2007-10-27
Same issue here as well.. Anyone resolve it yet?

---

### Post by Morientes on 2007-10-28
It has been solved with the latest update as far as I can see.

---

