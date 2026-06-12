---
title: "Asus w/ Nvida alternate install fails at select and install software"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by specopbookie on 2012-04-29
I cannot for the life of me, get this to install on my Asus ROG laptop with Nvidia GTS 360m Graphics card. I'm using the 64bit alternate install cd because of the nomodeset option (the desktop install crashes with a gpu lockup error right after you click install to hdd).
I'll get through most of the install, and then when the Select and Install Software step starts, it fails at 85%, then takes me back to the install menu. No matter how many times I try to retry that step, with or without selecting automatic updates, it'll fail and revert back. Skipping that step and finishing the install leaves me with broken install. I'm able to login to ubuntu via command line, but I can't do much from there. Another user around here reported that the alternate 64 cd has files that fail the checksum and break the installation.
[http://ubuntuforums.org/showthread.php?p=11877503](http://ubuntuforums.org/showthread.php?p=11877503) 
Maybe this is the case for me to? Any kind of assistance to get this installed would be much appreciated.


EDIT: FIXED. For all others having this same problem: The Pendrive USB program doesn't seem to like the alternate 64 iso. It won't create a valid ubs live image. Just burn it onto a disk, verify the md5, and it worked for me. Posted from inside Ubuntu 12.04 FTW!

---

