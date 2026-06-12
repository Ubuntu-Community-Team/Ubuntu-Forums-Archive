---
title: "Reverting a probably interrupted upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by tsr on 2008-10-31
Hi,

So I started to upgrade to 8.10 this morning before going to work. When I left there was just a few minutes left of downloading packages.

When I get home the comp doesn't start gdm but leaves me a message that I should contact the system admin to fix gdm.

Looking at it in a console it says something about
```
kinit: no image found at lots-of-giberish doing a normal boot
```

(This makes me believe that the upgrade didn't finnish (I have a crappy battery and powercable so I've set the comp to hibernate when it's running out of power) - as does the fact that the grub-menu gives me a lot of 8.04 options but no 8.10 option to choose a kernel)

The normal boot fails and it seems to be because my /-partition is mounted read only so a lot of processes can't get started.

Is there any way to either
a) remount / read-write so I can resume the dist-upgrade.
or
b) revert the upgrade

It's not such a big issue for me to reinstall everything as I have /home on a separate partition but somehow it would be nice to fix it in another way.

/tsr

---

### Post by utkjamie on 2008-11-01
I have a similar problem. Downloading upgrade packages took several hours and when I got back to my computer the screensaver lock had kicked in. I couldn't get past it because the unlock service was no longer running. No clue where it was in the upgrade process but I had no choice but to reboot the computer. Major fail.  See: [http://ubuntuforums.org/showthread.php?t=966124](http://ubuntuforums.org/showthread.php?t=966124)

Anyone have a solution?

---

### Post by bobromeo on 2008-11-01
> **utkjamie said:**
> .. Major fail...  have a solution?
When you start up you can choose a previous version, or better, the last version, in recovery mode, there is an option (dkpg) to finish an upgrade.

If you don't use grub, you should pres escape to get in this menu, I think ...

---

### Post by utkjamie on 2008-11-01
Okay, that seemed to work for me with the exception of a couple of packages. A few other things are screwy but they are probably best left for another thread.

Thanks!

---

