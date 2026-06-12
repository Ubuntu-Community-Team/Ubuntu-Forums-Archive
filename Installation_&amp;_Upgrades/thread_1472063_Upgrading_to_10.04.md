---
title: "Upgrading to 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2010-05-04
I just installed 10.04 from the Wubi, and I must say I'm not surprised.  This is the best Linux OS I've ever used.  It's very straight forward, user friendly, and the UI overhaul was a well deserved change from the classic Gnome.  I want to "upgrade" from Windows Vista to Ubuntu 10.04.  My problem is that I do not have an external media to back up my files to.  Is there a way to save those files without burning a million discs?  Maybe install Ubuntu on the free space, copy the files to the Ubuntu partition, and then delete the NTFS partition and resize Ubuntu's to take up the remaining space?  Can you resize Ubuntu's partition safely and efficiently after it has been installed?  Is there an "upgrade" option in the new installer to allow you to automate this process?  I just installed via Wubi and I'm not sure which parts are taken out of that installation.  Any help with this would be awesome.

---

### Post by rhm on 2010-05-04
There is always the option to have a dual-boot system installed, where you can opt to run either Linux or Windows when you first power up your computer. If this option is acceptable for you, the Live CD can create the Ubuntu partition during installation in the available free space, without touching your Windows system. The instructions are straight forward.

However, if you want a dedicated Linux system with no Windows anywhere, you will need external storage to backup your files before wiping everything out.

A third option that might work is installing Ubuntu alongside Windows, then fetching everything you want from Windows into Ubuntu. Then you delete the NTFS partition and install Ubuntu on it again (this should be possible). Re-fetch your files into the second Ubuntu installation, delete the first installation and its partition and finally resize the remaining Ubuntu partition to take up all the available space left. This is cockamamied at best, definitely time consuming and hardly worth the effort, but it's worth the shot if you really want to do it.

---

