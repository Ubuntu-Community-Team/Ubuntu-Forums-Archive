---
title: "[SOLVED] Update removed firefox 3?"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by csc2ya on 2008-07-12
ok...got a rather odd problem which has annoyed me somewhat.

I got the update icon on my panel earlier. I clicked, it and selected to install the updates it had found. Then, I got a message about a partial upgrade or something like that.

I thought it may have been part of the distribution upgrade, so I clicked the partial upgrade button to do it.

One of the things it's done, is removed firefox 3, along with all the favorites that I had saved in it.

I've tried reinstalling firefox 3 through synaptic, but that wants to remove ubuntu-desktop.

Additionally, it also appears to have updated avant window navigator, to a version that is broken, despite me having the old version locked in synaptic for precisely that reason. It is now not allowing me to downgrade it either.

---

### Post by theaxis69 on 2008-07-12
same firefox problem here

---

### Post by SkonesMickLoud on 2008-07-12
ubuntu-desktop is a metapackage that is safe to remove.  If you really want to, you can try reinstalling ubuntu-desktop after reinstalling FF.

Sorry I can't help you get your previous install back.  If you still have a folder named .mozilla in your /home (you can see hidden files [files/folders preceded by a .] by pressing Ctrl+H) then you may still have most of your settings when FF is reinstalled.

---

### Post by csc2ya on 2008-07-12
Thanks for the reply. I've just tried installing firefox 3 again, but i'm getting the following message every time:

firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed.

I've done a search in synaptic for xulrunner, and it's showing as already being installed. I've tried downgrading that, but that seems to want to remove a lot of things, which to be honest, i'm not too happy about having to remove, so i'm unsure what to do.

Also, I've looked in my home directory, and there is a hidden mozilla directory in there, although as to whether it contains my favorites, i'm unsure.

---

### Post by SkonesMickLoud on 2008-07-12
> **csc2ya said:**
> Thanks for the reply. I've just tried installing firefox 3 again, but i'm getting the following message every time:

firefox-3.0:
 Depends: xulrunner-1.9 but it is not going to be installed.

I've done a search in synaptic for xulrunner, and it's showing as already being installed. I've tried downgrading that, but that seems to want to remove a lot of things, which to be honest, i'm not too happy about having to remove, so i'm unsure what to do.

Also, I've looked in my home directory, and there is a hidden mozilla directory in there, although as to whether it contains my favorites, i'm unsure.

What does xulrunner want to remove?

---

### Post by aysiu on 2008-07-12
Can you post the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands? ```
cat /etc/apt/sources.list
cat /etc/lsb=release
```

---

### Post by csc2ya on 2008-07-12
The list that's giving me of things it wants to remove are:

gnome-userguide
startup-manager
ubuntu-desktop
ubuntu-docs
xulrunner-1.9-gnome-support
yelp

The only thing out of all of those that i've used in the past is startup-manger, but i've also had problems where i've gone to install one thing, and that complains about needing something else, which then needs something else that isn't available in the repositories.

---

### Post by csc2ya on 2008-07-12
> **aysiu said:**
> Can you post the output of these [terminal](http://www.psychocats.net/ubuntu/terminal) commands? ```
cat /etc/apt/sources.list
cat /etc/lsb=release
```

administrator@WinServ:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe #Added by software-properties
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main

## Avant Window Navigator
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe

## Galaxium Messenger
deb [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) hardy main

## AWN Development version
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

administrator@WinServ:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

### Post by gunashekar on 2008-07-12
Either avoid partial updates or check the list of packages that will be removed before allowing the update. Yes, update manager tried to remove firefox this morning on Hardy. I guess the developers are working on the problem and I would wait for it to be corrected. I thought such problems happen only when you are running alpha / development versions. Perhaps more care is needed before making updates on stable versions.

---

### Post by planet-reptile on 2008-07-13
I'm having the exact same problem. First the updates get messed up and now firefox get messed up. It would be nice if the programmers would check the code before they launch the updates.

---

### Post by grim4593 on 2008-07-13
Eh, I just updated a bit ago and according to Synaptic I have Firefox 3.0.1 wtf. That version doesn't even exist on the Mozilla site and just broke about half my extensions. When I tried to revert to the previous version in Synaptic, it wants to remove the same programs as mentioned earlier in the thread. :confused:

---

### Post by aysiu on 2008-07-13
Well, you have the proposed updates repositories enabled. That could be part of the problem, but it seems as if you have some other sketchy repositories too (an Intrepid Ibex one?).

I'd stick with the ordinary Main, Restricted, Universe, and Multiverse repositories, Reload, and then do an update with Update Manager.

---

### Post by Pettman on 2008-07-13
I got this problem on my laptop but not on my stationary computer, both run hardy but one is 32-bit and the other 64-bit.
After a bit of tinkering with the sources.list it seems like the problem is in hardy-proposed. Removing it and reloading the package list should let you install the updates.

EDIT: forgot to mention that this only happened on the 64-bit computer, the laptop.

---

### Post by pooyaplus on 2008-07-13
> **gunashekar said:**
> Either avoid partial updates or check the list of packages that will be removed before allowing the update. Yes, update manager tried to remove firefox this morning on Hardy. I guess the developers are working on the problem and I would wait for it to be corrected. I thought such problems happen only when you are running alpha / development versions. Perhaps more care is needed before making updates on stable versions.

Right, had this sort of problems, the best way as you said is to check the candidate packages for removal.

---

### Post by Master Chief on 2008-07-13
> **grim4593 said:**
> Eh, I just updated a bit ago and according to Synaptic I have Firefox 3.0.1 wtf. That version doesn't even exist on the Mozilla site and just broke about half my extensions. When I tried to revert to the previous version in Synaptic, it wants to remove the same programs as mentioned earlier in the thread. :confused:

Please check the following file about the update: 
```
/usr/share/doc/firefox/changelog.Debian.gz
```

Also enter *about:config* in the addressbar and look for "[COLOR="Red"]extensions.lastAppVersion[/COLOR]" that should give you a clue, maybe after a Google search?

---

### Post by pooyaplus on 2008-07-13
Hi,
Anybody checked this issue in the Bug pool? May be there's a solution or can be added to be considered by the dev team.:popcorn:

---

### Post by csc2ya on 2008-07-13
> **aysiu said:**
> Well, you have the proposed updates repositories enabled. That could be part of the problem, but it seems as if you have some other sketchy repositories too (an Intrepid Ibex one?).

I'd stick with the ordinary Main, Restricted, Universe, and Multiverse repositories, Reload, and then do an update with Update Manager.

Thankyou. That was the problem. I disabled all the repositories in update manager apart from the hardy ones, let it reload, then went into synaptic.

It then allowed me to install firefox 3 again, and on opening it, all my favorites are still there.

I think the reason I had the intrepid repositories in there was for avant window navigator, as something is broken in the latest version, although the version that I was using was the old hardy version.

Brilliant...found the problem with AWN as well. Despite having it locked in synaptic, I also had it set to update automatically, so it was still telling me that a new version was available. I downgraded it to the version that works, then disabled the auto update for it, and locked it to the version i'd downgraded to, and now it's nt bugging me about it every 5 minutes in update-manager

---

### Post by planet-reptile on 2008-07-13
Lukyli i havn't been using my 32bit computer for a while, so when i started it I unticked hardy-proposed in software sources, did a update and everything is as it should be. No problems with firefox and even the latest bug that added alot of sources in the third party section looked normal. So i would sugest to untick hardy-proposed. 
Proposed updates, are they important for the security?

---

### Post by grim4593 on 2008-07-13
> **Master Chief said:**
> Please check the following file about the update: 
```
/usr/share/doc/firefox/changelog.Debian.gz
```

Also enter *about:config* in the addressbar and look for "[COLOR="Red"]extensions.lastAppVersion[/COLOR]" that should give you a clue, maybe after a Google search?

Well according to the changelog and about:config, Firefox says its 3.0.1. Either way, I removed the Hardy Proposed repository. When I updated my sources quite a few of my programs are considered "local" including awn, firefox, some gnome files, gvfs, some libs, and a few other programs.

For Firefox I installed the Nightly Tester Tools extension and overrode the compatibility check on the extensions. Now everything works as expected.

---

### Post by Master Chief on 2008-07-13
> **grim4593 said:**
> ...For Firefox I installed the Nightly Tester Tools extension and overrode the compatibility check on the extensions. Now everything works as expected.

**[COLOR="Red"]extensions.checkCompatibility[/COLOR]** is your friend and all you need! Set it to false, and if you can't find it in about:config then just add it as a boolean pref ;)

---

