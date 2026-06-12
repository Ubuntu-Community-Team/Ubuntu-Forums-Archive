---
title: "Screen blanks after Xubuntu install"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Punk Boi 8 on 2007-10-04
I have just installed Xubuntu 7.04 from the alternate install, and i get a command line boot script, then the screen blanks. How can I fix this? Thanks!

---

### Post by Pumalite on 2007-10-04
Try:
Ctrl+Alt+F1 to get command line, then at the command line:
sudo dpkg-reconfigure xserver-xorg (if you have really finished installing the system)

---

### Post by Scunizi on 2007-10-04
After doing Pumalite's suggestion you should also do a "sudo apt-get update" then "sudo apt-get upgrade" then sudo apt-get dist-upgrade.. I found that out the hard way today installing xubuntu desktop on my server..

---

