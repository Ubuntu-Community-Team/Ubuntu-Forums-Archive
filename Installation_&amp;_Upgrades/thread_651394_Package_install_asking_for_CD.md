---
title: "Package install asking for CD"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by kwandtke on 2007-12-27
I'm trying to install a package via apt-get ... at one point the system stops and prompts " Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

I've run into this before .. so I load the CD .. but then I get the same prompt back.  I ran VOLNAME and my cd is not named Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016) but Ubuntu-Server 7.10  i386 ... 

could this package be looking for that specific volume name on the CD?  Other than burning another is there a way around this?

---

### Post by taurus on 2007-12-27
Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom.  Save it with <Ctrl>o and exit with <Ctrl>x.  

Then run

```
sudo apt-get update
```
Now, try to install whatever you planned before and it wouldn't ask you to insert the installer CD anymore.

---

### Post by kwandtke on 2007-12-27
Thanx .. that did the trick.

---

