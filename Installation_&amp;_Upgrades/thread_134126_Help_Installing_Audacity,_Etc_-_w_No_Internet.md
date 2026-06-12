---
title: "Help Installing Audacity, Etc - w/ No Internet"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by svilledoc on 2006-02-21
I have installed 5.1 with no problems. When I try to activate the Universe repository it seems that the program is trying to look on the internet and it says that it can't find some info that it needs. Is it possible to install applications without being connected to the internet? I thought that all of the universe programs were contained on the installation CD.

---

### Post by snowjunkie on 2006-02-21
You can add the install CD as a repository and try that - it's usually commented out of the first line of your sources.lst.  You should comment out the rest as you do need internet access for those.  If you need something that is not available on the install CD, you can download it on another computer, burn it to CDROM and bring it over to your ubuntu box that way.

---

### Post by christhemonkey on 2006-02-21
No , the extra repositories are not on the CD, they are all collected in one (or maybe several!) places on the internet.
To get audacity and others, go on your internet computer to this page:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Search for the package you want, and then save it onto a floppy or CD or usbstick or whatever.
Then copy it onto your ubuntu desktop or in your home folder.
Then in a terminal;
type ```
cd /wherever/you/put/thepackage.deb
```
```
sudo dpkg -i thepackage.deb
```
Replacing thepackage.deb with the actual name of the .deb!
This should install it and set it up fine.
You probably will need to get lots of dependencies for various things to work, but these are listed on the website ([http://packages.ubuntu.com/](http://packages.ubuntu.com/))

---

