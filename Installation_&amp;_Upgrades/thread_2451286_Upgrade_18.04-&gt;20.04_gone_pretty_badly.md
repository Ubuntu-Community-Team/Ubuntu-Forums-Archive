---
title: "Upgrade 18.04-&gt;20.04 gone pretty badly"
date: 2020-10-01
forum: Installation &amp; Upgrades
---

### Post by udippel on 2020-10-01
(I wonder: should I do individual messages, or write down everything in one go? - This is no bug report, so I give it a single go:)

0. I didn't want to upgrade. I only had a standard daily apt-get with 'dist-upgrade' working; which at any moment in the past didn't actually do that; I simply had applied that for convenience: It wouldn't ask for additional packages. Yesterday, there wasn't even a question popped up, if I really wanted to upgrade to 20.04; bang, 'apt-get dist-upgrade' and there it was. Over.

1. It used to be a dual boot with W10 before, after the upgrade, it is just a (k)ubuntu 20.04. No more grub selection menu.
-> (Remains unsolved, though:) I checked the BIOS (lenovo Helix 2), and found the ubuntu drive as first boot device, Windows boot loader second, and so forth. So it seems to correctly point to the correct device, I guess. So I can boot to W10 by selecting temporarily the W10 boot loader.

2. Touchpad didn't do the double-tap any longer; had to tap + left mouse button. Solved by finally finding a solution: editing /usr/share/X11/xorg.conf.d/40-libinput.conf

3. I had a left edge mouseover leading to the 'show desktop' which is still set, but doesn't work any longer.
-> This one I could solve: The compositor was disabled (NOT by me!); and System Settings->Display and Monitor->Compositor>Enable could solve this matter with a reboot.

4. The speakers in my tablet are 'dead'. They are visible, but produce nothing.

That's it what I encountered until now. 
I'd be most happy to hear solutions for 1,3 and 4.

Kind regards,

Uwe

---

### Post by ajgreeny on 2020-10-01
I don't understand how running  that dist-upgrade command managed to move you from 18.04 to 20.04, though I am aware that the option in the update manager has only recently appeared, a bit later than usual.

Can you double check that you're now on focal and show us your active repos with command ```
cat /etc/apt/sources.list
```

---

### Post by udippel on 2020-10-01
Sure, here is what it looks like now:

```
$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal main restricted
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal-updates main restricted
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
$
```

I DID try the  sudo do-release-upgrade -m desktop a number of times in the past; just to SEE if the update was finally available. I was willing to update,  but not in this moment of time, while I am very busy with my lecturing tasks. A number of times it failed, last time it did something; but I Ctrl-C it out immediately as I knew it would be ready by then. Any background job keeping running? 
In any case, I'd expect to be asked at least once "Are you sure ...?"  Before, it had also informed me about commenting out certain third party software and stuff. Yesterday sudo apt-get dist-upgrade just downloaded 2300+ packages, done.

Uwe

---

### Post by ajgreeny on 2020-10-01
You either need to manually edit the /etc/apt/sources.list file, removing the # at the start of all lines beginning ***# deb-src*** or, quicker and simpler for most users, enable source repos in the software sources application.

---

### Post by Impavidus on 2020-10-02
> **udippel said:**
> ... last time it did something; but I Ctrl-C it out immediately as I knew it would be ready by then. ...

That explains it. do-release-upgrade changed the software sources to focal and began calculating the upgrade, then you killed it with ctrl-c but didn't restore the original software sources from backup. So the next time you ran apt-get, it checked the focal repositories and performed the release upgrade.

---

