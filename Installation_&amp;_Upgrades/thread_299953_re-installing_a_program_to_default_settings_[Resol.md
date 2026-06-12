---
title: "re-installing a program to default settings [Resolved]"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by jlipoth on 2006-11-15
I installed VLC media player in Edgy, and was enjoying it with out problems until I decided to customize some of the settings, skin it, etc.  now I cannot get VLC to run.  I've tried reinstalling and uninstalling-rebooting-installing and nothing seems to work.  I was wondering if it would be possible to wipe out any left over config files for VLC so that I can do a clean install, or if there is any other way to fix this problem?  I am pretty new to Ubuntu-Linux(yet another guy wanting to retire his "Windows" ways), but I am happily willing to learn - the more I've learned the more I like it!

---

### Post by penguin.ch on 2006-11-15
Jlipoth,

in Synaptic, you may select to *completely remove* (instead of "remove" only, which is the default) the package in question. This is supposed to result not only in the removal of the installed files, but also in the removal of (hopefully) all according configuration files ...

HTH
Birdy

---

### Post by aysiu on 2006-11-15
Try pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/.vlc ~/.vlc.old
```

---

### Post by jlipoth on 2006-11-15
I used the terminal command to move the directory first as it looked like it took the least effort :) .  That worked great!  I also took a look around synaptic and found some cool plugins for xmms!  Thanks for all the help!

---

