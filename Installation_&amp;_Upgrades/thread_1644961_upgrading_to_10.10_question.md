---
title: "upgrading to 10.10 question"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by limjix on 2010-12-13
I have read this tutorial [http://www.unixmen.com/news-today/1147-how-to-upgrade-to-ubuntu-1010-maverick-meerkat-from-ubuntu-1004-lucid-karmic-desktop-a-server](http://www.unixmen.com/news-today/1147-how-to-upgrade-to-ubuntu-1010-maverick-meerkat-from-ubuntu-1004-lucid-karmic-desktop-a-server) and i got a few questions.

1. Will by upgrading, erase my partition and reinstall ?

2. I am currently using 32 bit ubuntu but for the next upgrade i plan to go 64 bit, i believe the tutorial is 32 to 32 , how do i do 32 to 64?

Thank you!

---

### Post by Quackers on 2010-12-14
I may be wrong, but I'm not sure you can upgrade from 32 bit 10.04 to 64 bit 10.10
I would imagine that you would need to download the 64 bit 10.10 iso, burn a disc or usb and re-install.
Maybe somebody else could confirm?

---

### Post by limjix on 2010-12-14
Does it make sense if i upgrade my 10.04 to 64 bit first then only upgrade to 10.10?

---

### Post by plucky on 2010-12-14
> **limjix said:**
> Does it make sense if i upgrade my 10.04 to 64 bit first then only upgrade to 10.10?

You cannot upgrade from 32-bit 10.04 to 64-bit 10.04.

You have to do a clean install of the 64-bit system.

So if you are going to upgrade to 10.10,you might as well do a clean install of 64-bit 10.10.If you don't like upgrading,stick with 10.04 LTS.

Good Luck

---

### Post by oldfred on 2010-12-14
If you do not have a separate /home or /data and good backup of the hidden files & folders in /home you should do that before installing the 64 bit version. If you have 20GB to spare on harddrive just create a new / (root) partition to install to.

Applications are not in /home even though all the settings are. You can export a list of iinstalled apps and from that list reinstall the latest (and 64bit) versions.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

