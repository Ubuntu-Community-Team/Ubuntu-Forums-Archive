---
title: "libreoffice"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by rye37 on 2011-06-14
I've downloaded it, extracted it, and gone through the procedure to install it. It appeared to have installed, but it doesn't appear on the main menu, and I don't know how to find it

---

### Post by SoFl W on 2011-06-14
from the terminal type "soffice" and see if it starts, that way you know it is installed.

---

### Post by mörgæs on 2011-06-15
In general one should not download and install software from outside sources. 

If you are on 11.04, Libre Office is in the repositories.

---

### Post by silentstone on 2011-06-15
I was able to install LibreOffice on Ubuntu 10.04 through a PPA--it gives the benefits of automatic updates and distro testing/integration.  The command was something like:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update 
sudo apt-get dist-upgrade
```I'm not on my ubuntu box right now to double check, but IIRC, installing libreoffice this way wants to remove openoffice first, so that last line (...dist-upgrade) allows this by recognizing libreoffice as a new program that conflicts with or obsolesces the openoffice program.  Still working from a fuzzy memory here, but I was alarmed by how many programs wanted to be removed in this process.  I think I did a 
```
sudo apt-get purge openoffice 
sudo apt-get install libreoffice
``` to try to limit changes to my system.

More info's in the wiki: [https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice)

Disregarding all this, if "soffice" runs the program, but you can't find it anywhere in the menu, then the version that you installed probably didn't include .desktop files to automatically add LibreOffice to the desktop menu.  You can double-check what got installed by browsing to whatever folder the .deb you downloaded/extracted is in, and:
```

dpkg-deb --contents <name-of-package-file>
```

---

### Post by Hagar Delest on 2011-06-17
Better use the vanilla versions IMHO (PPA is not officially maintained). See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) The same process applies for LibO (I run both on my 11.04 system).

---

