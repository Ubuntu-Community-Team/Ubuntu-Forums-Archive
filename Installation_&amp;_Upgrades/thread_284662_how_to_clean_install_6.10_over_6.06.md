---
title: "how to: clean install 6.10 over 6.06"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by acerlinux on 2006-10-25
same question as the title.

btw, if I use the update manager to update, is it a clean install or all my settings will be still there?

Thanks

---

### Post by Kateikyoushi on 2006-10-26
If you use the upgrade manager your settings are kept, use the cd to install and format the partitions to make sure you end up with a fresh install.

---

### Post by aysiu on 2006-10-26
If you want to do a clean reinstall, you should [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome).

If you do a regular upgrade, your settings and programs will all be intact.

---

### Post by maddbaron on 2006-10-26
if u upgrade, setting are kept? even wireless? I think i'll upgrade n burn an iso just incase but can u repartition in an upgrade?

---

### Post by shappen on 2006-10-26
clear up the config files in your home dictory

---

### Post by gerowen on 2006-10-26
How are you guys downloading it?  I'm finding the "Release Candidate" but I'm not finding the official release, even though the front page has been updated for it.

---

### Post by aysiu on 2006-10-26
If you update to the release candidate and then update again tomorrow, you'll have the final version.

---

### Post by gerowen on 2006-10-26
Well right now 6.06 is non-functional, I can't get X to start, it just says, "No Screens Configured" even though I've tried everything in the world.  ([See my topic on it](http://www.ubuntuforums.org/showthread.php?t=284468)).  Anyway, I'm downloading the RC for Edgy, and you're saying if I install this I can update to the full release via synaptic?

---

### Post by Cynical on 2006-10-26
yes

---

### Post by gerowen on 2006-10-26
Sorry for being a total Ubuntu noob, but I just now got 6.06 working and have a question.  I know that I can upgrade if I'm using 6.10 RC, but is it possible to upgrade to 6.10 from 6.06 via synaptic or something without downloading and burning another CD?

---

### Post by Cynical on 2006-10-26
yes using this command,

```
gksu "update-manager -c -d"
```

---

### Post by acerlinux on 2006-10-26
> **Cynical said:**
> yes using this command,

```
gksu "update-manager -c -d"
```

gksu "update-manager -c"

is OK now, the 6.10 has been released.

I just upgraded to 6.10 right now.

but I cannot start the X server now, I believe the problem is about my ATI M7500 video card, some one know how to solve it?

---

### Post by Tasu on 2006-10-26
on another post I can't find anymore is stated that you have to install the metapackage for all drivers in order to have X starting... oh! Man! This is really a big bug for the upgrade process...
however, from terminal:

sudo aptitude install xserver-xorg-video-all

I think this was the package...

---

### Post by acerlinux on 2006-10-27
> **Tasu said:**
> on another post I can't find anymore is stated that you have to install the metapackage for all drivers in order to have X starting... oh! Man! This is really a big bug for the upgrade process...
however, from terminal:

sudo aptitude install xserver-xorg-video-all

I think this was the package...

Yep, that is the issue, I ignored the Xorg log when I changed "flgrx" back to "ati", it said "ati" was not installed but not cannot find screens. after E installed the "ati" driver, the x server could start properly, obviously the 3D effects will not work](*,) . is there any solution for this problem?

for me, I use ATI mobility 7500 so I install the xserver-xorg-driver-radeon is OK. Thanks Mate.

another question is that, do the crash reports will be generated in /var/crash/ only? And Can I just simply delete those files safely??:confused: 

Thanks again.

---

