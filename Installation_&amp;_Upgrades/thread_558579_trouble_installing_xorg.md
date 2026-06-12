---
title: "trouble installing xorg"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by animasana on 2007-09-24
hi everyone.
installed command line system of 7.04 using my cdrom drive on a toshiba 3480ct. (p3 600 w 64mb ram)

server runs perfectly; using this guide to get a graphical interface up and running

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

when i > apt-get install xorg calculates all new packages to install, then asks me if i want to continue, and THEN says:

Media Changeö please insert the disc labeled 'Ubuntu 7.04 _Fiesty Fawn_ - Release i386 (29979415) ' in the drive '/cdrom/' and press enter.

I enter the same CD i used for my install 10mns ago, and then press enter. It prints the same request again and again. 

any thoughts on what I can do? if I cannot use the cdrom, is it possible to get all the archives from the internet? (ie NOT use teh cdrom drive at all?) 

what commands should i use? other ideas?
thanks!

---

### Post by animasana on 2007-09-24
found the solution!

[http://ubuntuforums.org/showthread.php?p=3413170](http://ubuntuforums.org/showthread.php?p=3413170)

thanks!

---

### Post by Compyx on 2007-09-24
You should comment-out any references to the CD-rom in [FONT="Fixedsys"]/etc/apt/sources.list[/FONT]. A line like:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)]/ gutsy main restricted
``` is probably what you're after. Just stick a '#' in front of the line, save the file and try to install xorg again.

---

