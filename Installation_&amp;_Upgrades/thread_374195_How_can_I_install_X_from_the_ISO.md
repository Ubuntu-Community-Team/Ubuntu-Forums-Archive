---
title: "How can I install X from the ISO?"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Carlos Santiago on 2007-03-02
After a very unusual problem ([http://ubuntuforums.org/showthread.php?p=2235546)](http://ubuntuforums.org/showthread.php?p=2235546)), I need to install X Window without booting from CD.
My CD-ROM is broke!
I am sure it is possible, but I don't have the faintest idea how to do it.
Any help would be very much appreciated?

---

### Post by zvacet on 2007-03-02
Try via net and I think command is
```
sudo apt-get install X-server
```

---

### Post by Carlos Santiago on 2007-03-02
Thanx zvacet. Btw, do you know how to install from an Ubuntu ISO file?

---

### Post by zvacet on 2007-03-02
Only if you have alternate CD.
```
sudo apt-cdrom add
```
```
sudo aptitude
```
Maybe before you start reed in system>help>sytem documentation>Server administration and maintenance>package managment>aptitude

---

