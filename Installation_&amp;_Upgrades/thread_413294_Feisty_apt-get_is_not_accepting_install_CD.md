---
title: "Feisty apt-get is not accepting install CD"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by joepie on 2007-04-19
did an online upgrade, 6.10 to 7.04 that failed on, cant acces TTY.
Next, downloaded the Feisty server CD, fresh install, networking fixed (didn't work after install), 
online update.. succes
download madwifi driver ... succes.
Need:
sudo apt-get install build-essential linux-headers-server 
need to get 21.8 mb of files
continue Y
Media change: please insert the disc labeled  i386 (20070415)
in the CD rom , press enter
system hangs
is not accepting the installer CD anymore,
I checked the CD again for errors, no errors on the CD.

Suggestions ? 

Thanks

Joepie

---

### Post by joepie on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=395391](http://ubuntuforums.org/showthread.php?t=395391)

You have to comment out the cdrom reference in /etc/apt/sources.list


{{CLOSED}}

---

