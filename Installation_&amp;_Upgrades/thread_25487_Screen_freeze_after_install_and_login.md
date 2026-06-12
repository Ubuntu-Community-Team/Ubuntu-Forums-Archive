---
title: "Screen freeze after install and login"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Oam on 2005-04-10
Hi!

Ubuntu newbie here! I have been using Fedora Core 1,2 and 3 more or less frequently in the past year but now I wanted to try something else. 

Ubuntu installed fine and soon enough it gave me my first login screen. However, after I key in the password the screen just stalls. Mouse works but nothing happens for at least an hour (I didn't wait longer). It gives no errors, nothing. 

So, any tips on how to proceed?  It gives me a very high resolution screen with full colors so at least it seems that my nvidia card is recognized.

Recovery mode worked but I didn't get any bright ideas what to do there...


My system is:
- Abit Nforce2 with soundstorm 
- 1Gb RAM
- Athlon XP 2500
- GeForce 6800LE gfx
- 80Gb Maxtor SATA & 30Gb Seagate IDE
- DVD+-RW drive
- Pixeview(?) bt878+ PCI Tv-card
- Logitech webcam in USB
- USB 6in1 card reader

---

### Post by erkki70 on 2005-04-10
Hi,
Have you seen this thread?
[http://www.ubuntuforums.org/showthread.php?t=23252](http://www.ubuntuforums.org/showthread.php?t=23252)

Hope this helps and good luck.

Cheers,
Erkki

---

### Post by Oam on 2005-04-10
[QUOTE=erkki70]Hi,
Have you seen this thread?
[http://www.ubuntuforums.org/showthread.php?t=23252](http://www.ubuntuforums.org/showthread.php?t=23252)

Hope this helps and good luck.

Cheers,
Erkki[/QUOTE]
 I think I might be facing this bug:
[http://www.ubuntuforums.org/showthread.php?t=24703](http://www.ubuntuforums.org/showthread.php?t=24703)

Because reinstall with no acpi didn't help.

---

### Post by Oam on 2005-04-11
[QUOTE=Oam]I think I might be facing this bug:
[http://www.ubuntuforums.org/showthread.php?t=24703](http://www.ubuntuforums.org/showthread.php?t=24703)

Because reinstall with no acpi didn't help.[/QUOTE]
 Ok, it was a display driver bug/feature/overlook. 

I installed the latest nvidia stuff with apt-get and changed manually xorg.conf to use driver "nvidia" instead of "nv". I also commented out DRI section (I remember that was something that I had to in Fedora too). Now the system works! :)

---

