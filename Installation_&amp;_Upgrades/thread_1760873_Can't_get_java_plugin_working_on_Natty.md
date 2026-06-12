---
title: "Can't get java plugin working on Natty"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by gribbsy on 2011-05-17
Hi.  I am just trying out Natty for the first time.  I'm having trouble installing sun-java.  The iced-tea plugin which comes with firefox just doesn't cut it for pogo card games.

I seemed to have installed it correctly because when I check my Software Manager there is a green check on all of the sun java6 stuff.  But when I go to tools/addons/plugins the only thing there is the icedtea (no sun java6 plugin).  I may have to go back to using linux mint.

Any help would be appreciated I'm at wit's end.:confused:

---

### Post by wildmanne39 on 2011-05-17
> **gribbsy said:**
> Hi.  I am just trying out Natty for the first time.  I'm having trouble installing sun-java.  The iced-tea plugin which comes with firefox just doesn't cut it for pogo card games.

I seemed to have installed it correctly because when I check my Software Manager there is a green check on all of the sun java6 stuff.  But when I go to tools/addons/plugins the only thing there is the icedtea (no sun java6 plugin).  I may have to go back to using linux mint.

Any help would be appreciated I'm at wit's end.:confused:
Hi, the easiest way if you have not installed the media stuff to play and rip dvds is to go here and follow the instructions for the version of ubuntu you use because it will take care of it all at the same time.[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by 67GTA on 2011-05-17
Ubuntu defaults to iced tea even when sun-java is installed. The easiest way is to simply uninstall anything having to do with icedtea/jdk. This will force the sun-java version to be used. Another way is to run ```
sudo update-alternatives --all
``` in a terminal and select your system defaults.

---

