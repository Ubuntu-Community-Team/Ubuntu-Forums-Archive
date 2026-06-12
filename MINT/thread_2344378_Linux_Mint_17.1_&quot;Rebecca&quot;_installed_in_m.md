---
title: "Linux Mint 17.1 &quot;Rebecca&quot; installed in my computer I could not run the Deskjet ink ad"
date: 2016-11-24
forum: MINT
---

### Post by ustunerdil on 2016-11-24
Linux Mint 17.1 "Rebecca" installed in my computer I could not run the Deskjet ink advantage 2060 all-in-one K110 printer ?

---

### Post by QIII on 2016-11-24
*Moved to **MINT***

---

### Post by oldfred on 2016-11-25
Do not know about Mint, but Ubuntu usually has a somewhat older HPLIP which works fine if you have an older HP printer.

But if a newer printer you need to download directly from HP.

With my older install and then new HP printer.
You have selected Ubuntu 14.04 using the HP Envy 4500 E-all-in-one.
Ubuntu 14.04 supplies HPLIP 3.11.5 by default, which does not support your printer.
You must ensure latest HPLIP version (recommemded), or at least HPLIP 3.13.6 in order to use your printer with Ubuntu 14.04.
Creates lots of folders & files, best if in its own sub-directory

HPLIP issue on 14.04 - manual download of plugin to solve
[http://ubuntuforums.org/showthread.php?t=2230875](http://ubuntuforums.org/showthread.php?t=2230875)
HP printers broken in Linux? Here's a fix. 
[http://www.dedoimedo.com/computers/linux-hp-printing.html](http://www.dedoimedo.com/computers/linux-hp-printing.html)


[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

---

