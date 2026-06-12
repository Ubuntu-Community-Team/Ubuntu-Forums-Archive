---
title: "Computer crashed while upgrading from 7.04 to 7.10"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Gnufsh on 2007-11-25
While I was running the upgrade tool upgrading from 7.04 to 7.10, my computer screen went to blank with a blinking cursor. After trying to different virtual consoles without success, I hit the power button without really thinking. The upgrade was in the middle of installing files, although the hdd activity light had been off for quite some time when the computer powered off. It starts up fine, but is there any way to resume the upgrade process?

Dan

I'm using kubuntu, by the way

---

### Post by Gnufsh on 2007-11-26
I ran  sudo dpkg --configure -a and sudo apt-get install -f, itfound a few packages that ould be removed, you I used the autoremove function of apt-get. I'm not sure what else to try here. I don't have any major problems, except the lack of a bootsplash (I just have a blank screen until X starts).

---

