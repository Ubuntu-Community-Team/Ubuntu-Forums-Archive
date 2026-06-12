---
title: "Ubuntu crashes on first time login"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by cookf on 2005-02-17
Hi, I've got a laptop (whitebox, 95MB RAM, 6 GB partition, SVGA LCD) and got an official CD set: test bootable CD, and installation CD. 

The bootable CD ran fine (bit slow) so I decided to put UBUNTU next to WinME :-P . The installation procedure runs without problems but at the graphical login screen it freezes (screen half loaded). I can run UBUNTU is save mode (text screen) but don't know how search for clues why it crashes. As it ran the bootable CD version, it shouldn't have problems with the graphics.

Any suggestions where to look for log files or other clues?

Thanks

Frank

---

### Post by CyrilleMortreux on 2005-02-17
[QUOTE=cookf]Hi, I've got a laptop (whitebox, 95MB RAM, 6 GB partition, SVGA LCD) and got an official CD set: test bootable CD, and installation CD. 

The bootable CD ran fine (bit slow) so I decided to put UBUNTU next to WinME :-P . The installation procedure runs without problems but at the graphical login screen it freezes (screen half loaded). I can run UBUNTU is save mode (text screen) but don't know how search for clues why it crashes. As it ran the bootable CD version, it shouldn't have problems with the graphics.

Any suggestions where to look for log files or other clues?

Thanks

Frank[/QUOTE]

Live CD is working fine ?

So boot with this one and try to copy on your hard drive disk (or print it) the /etc/X11/XF86Config file generated with the live CD

And then, compare it to the one made during the install process. Must have somethong wrong. 

At least, you need a swap slice about 200Mo (95Mo memory x2) in order to have X starting and working.

You can also try to reconfigure your xfree server as root (or sudo)

dpkg-reconfigure xserver-xfree86

---

### Post by cookf on 2005-02-18
I'll go to work on it tonight. Can only post result after weekend, or not if all goes well.

Thanks Frank

---

