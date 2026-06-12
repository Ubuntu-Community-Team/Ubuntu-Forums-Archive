---
title: "Problems after migrating Ubuntu to another drive"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by ld.4lpha on 2013-03-21
I had a failing drive, so I copied all of the directories under / (with the exception of /home, /media, /proc, /lost+found...) to another drive.  The target drive already had a system installed, which I overwrote but wanted to keep the /home on it.  

After doing this, I rebuilt grub and now it boots as expected except for the fact that it always drops to low graphics mode after failing to detect display (drivers?), input devices, etc.

Anyone have an idea of what might have happened during this move?

Thanks!
LD

---

### Post by gordintoronto on 2013-03-21
Many settings are stored in hidden files in /home

You didn't copy over /home, so the settings are from the old system -- and perhaps in the wrong format.

Also, if you didn't delete everything in /etc, for example, files from the old install are still around. Ubuntu has a few configuration files which will be used if found -- but they are not part of a basic install. I think xorg.conf is one of those...

---

### Post by ld.4lpha on 2013-03-22
Interesting.  I didn't realize that files required for booting were stored in /home.

Thanks for the info!

---

### Post by ahallubuntu on 2013-03-22
~

---

