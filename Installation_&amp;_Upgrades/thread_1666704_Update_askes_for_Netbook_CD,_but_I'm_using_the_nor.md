---
title: "Update askes for Netbook CD, but I'm using the normal desktop version"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by Namibnat on 2011-01-14
I've recently installed Ubuntu 10.10 as a fresh install, and I've had more problems with it than any previous Ubuntu installation.

One thing that keeps plaguing me is that I don't seem to be able to get the updates to run properly.  I kept getting error messages with the normal gui automatic upgrades and so I've switched that off (with the startup apps) and tried to run the updates with the console.

Strangely, when I try this, I get this message:
[INDENT]Ign cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4) lucid Release.gpg
Media change: please insert the disc labeled                                   
 'Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)'
in the drive '/cdrom/' and press enter
[/INDENT]But I'm not running Ubuntu Netbook, and I'm on 10.10, not 10.04

---

### Post by garvinrick4 on 2011-01-14
#Open a terminal:
```
gksudo gedit /etc/apt/sources.list
```#See line on top that the starts with #deb cdrom:
Make sure that line in yours has the comment sign "#" (without qoutes) and hit save.
#A screenshot below: Strange you used a 10.10 disc and error message with 10.04 like you upgraded from.
Something though is wrong with sources.list if fix does not work. Post your sources.list here.

---

### Post by Namibnat on 2011-01-14
Thank you, that solved my problem.

---

### Post by garvinrick4 on 2011-01-14
No problem, enjoy your Ubuntu.

---

