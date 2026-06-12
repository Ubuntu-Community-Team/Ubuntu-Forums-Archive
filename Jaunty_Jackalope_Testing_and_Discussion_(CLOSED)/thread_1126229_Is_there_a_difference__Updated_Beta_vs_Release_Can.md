---
title: "Is there a difference?  Updated Beta vs Release Candidate"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bthoward on 2009-04-15
If someone has installed the Beta and has performed all updates is that the equivalent of installing form the RC?  

I've installed a machine from Beta for my dad cause his Bday is just before release and I'd like to know if I should redo it for him later when the release drops...

I've seen some strange issues here and there... The weirdest of which was when I was using the computer just randomly the computer played the little drum beat and poof I was at a login prompt.  I logged in and it was like the computer had just rebooted.  Was almost like I'd done a CTRL+ALT+BKSP but I didn't...  I've not needed it yet in 9.04 but if I remember reading correctly I think its disabled in this version.  Something I'll probably go in and turn back on.

---

### Post by jmmL on 2009-04-15
Yes, the updated beta will be the same as the RC, and an updated RC will be the same as the gold version.

---

### Post by bthoward on 2009-04-15
And from that same logic an updated beta is identical to a gold copy right?  Fairly certain of this but I know that when I upgrade from one version to the next that its not the same as doing a fresh install of the newer version.

---

### Post by dirtylobster on 2009-04-15
I would guess that upgrading leaves some bloat around but not enough to notice.

---

### Post by MacUntu on 2009-04-15
> **dirtylobster said:**
> I would guess that upgrading leaves some bloat around
Not necessarily but possible.

---

### Post by ssam on 2009-04-15
it is possible that there will be difference due to installer bugs, or buggy programs leaving rubbish files around.

that back to login screen issue is most likely the X server crashing.

you should file a bug report. see
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://wiki.ubuntu.com/DebuggingXorg](https://wiki.ubuntu.com/DebuggingXorg)

---

### Post by OrangeCrate on 2009-04-15
> **dirtylobster said:**
> I would guess that upgrading leaves some bloat around but not enough to notice.

I would doubt it, and upgrading is the recommended way of moving from one version to another.

> Actually, We do NOT advise a clean install every time you want to upgrade. The upgrade path receives far more testing and attention than the clean install path. The official recommended method for moving to a new version of Ubuntu is to use a supported upgrade procedure!

jdong, post #96, here:

[http://ubuntuforums.org/showthread.php?p=6063808](http://ubuntuforums.org/showthread.php?p=6063808)

-----

Edit:

And see here, for some info on routine cleaning up of junk files:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Zorael on 2009-04-15
> **bthoward said:**
> And from that same logic an updated beta is identical to a gold copy right?  Fairly certain of this but I know that when I upgrade from one version to the next that its not the same as doing a fresh install of the newer version
For any given release (8.04, 8.10, 9.04, 9.10, etc) developers decide on what applications to include per default, and their "main versions", if that makes sense. They keep to these apps throughout the development cycle, and only update them with bug fixes and not major version upgrades such as OpenOffice 2.x -> 3, or KDE 3.5.x -> KDE 4.

*Inbetween* releases, however (Intrepid -> Jaunty, Jaunty -> Karmic), they're free to sync with the latest in Debian as well as perform general design decisions. So you won't suddenly see your notification system getting a major overhaul mid-Intrepid as opposed to in the development of Jaunty.

When installing fresh, a bunch of configuration files are copied straight from the installation medium as opposed to fetched from the repositories. As a concrete example, a KDE 3.5.x installation (at least, not sure about KDE4) behaves slightly different if installed via kubuntu-desktop as opposed to installing via a proper Kubuntu live environment, since it's not copying those configuration files.

Moreover, old packages are retained that might not have *meant* to be part of the new release. Imagine if they suddenly, in Karmic, decide to get rid of PulseAudio. Every upgrader will still have it installed, and there'd be some major clamoring and bug reports filed when new stuff in the repositories don't expect sound to be handled by it. "Flash doesn't play sound after upgrade", "No sound in Rhythmbox/Exaile anymore", etc.

The sole exception is backports, and the wiki entry for it is a good read. See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).

---

### Post by MacUntu on 2009-04-15
> **SSam said:**
> you should file a bug report.

That's not so easy. What if a folder contains user data or a "~"-backup from editing a file? Many programms omit to remove such non-empty folders but in most cases that's wanted and therefor not bug-like behavior.

> **OrangeCrate said:**
> jdong, post #96, here:

The upgrade path from release to release but for sure not the upgrade path from some development milestone to the final. 

I'd definitely upgrade from an updated final Ubuntu-1 to a final Ubuntu without any hesitation.

---

