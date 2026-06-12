---
title: "Installer crashed"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by JamesR404 on 2010-07-28
Hi all,


I want to install Ubuntu next to my Windows 7 installation. I boot up Ubuntu from USB stick and proceed with the installation, I formatted one partition "fs ... 2" (something ending on 2) and marked it bootable with a /

The installer seems to go OK almost all the way through the end, then I receive these errors and Ubuntu isn't installed:

[IMG]http://dl.getdropbox.com/u/185326/And%202nd%20error.png[/IMG]
[IMG]http://dl.getdropbox.com/u/185326/Fatal%20Install%20error.png[/IMG]

Any hints to resolve this would be most appreciated. If you need more information, also just let me know.


Muchas gracias!
-James

---

### Post by quixote on 2010-07-31
I assume you're trying to install Lucid?  I don't know how well it does on ext2 filesystem.  (I know.  That's the default.  Dumb, is all I can say.)  Try selecting ext4, and see whether that works.  If not, consider making another download of the iso, and re-doing the LiveUSB.  Maybe something went wrong in that process and the instlal media you're trying to use are just bad.

---

### Post by JamesR404 on 2010-08-09
Hi, thanks for your advice!

The version of Ubuntu I'm trying to install is this one:
[http://www.eeebuntu.org/index.html](http://www.eeebuntu.org/index.html)

I'll follow your steps and see if that helps, will keep you posted! Thanks :D

---

### Post by Pumalite on 2010-08-09
Check the md5sum of the ISO you are downloading before burning. For burning in Windows; I recommend downloading and installing and installing a free program called ImgBurn. Burn as an IMAGE at 4x or less. (Mode>ISO )

---

