---
title: "[SOLVED] how to upgrade properly to ubuntu 7.10 studio"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by famous3warriors on 2007-12-06
Right night I have Ubuntu 7.10 i386 and would like to upgrade to Ubuntu studio 7.10 i386 properly how do I proceed with this venture.  Thanks for your help. It is greatly appreciated.

---

### Post by Drunky on 2007-12-08
I used this [Ubuntu Help wiki page]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") to upgrade from Ubuntu 7.10 to Ubuntu Studio 7.10.

Open a terminal and copy & paste:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

This gives you a full installation of Ubuntu Studio including the real-time kernel.

---

### Post by famous3warriors on 2007-12-08
Thank you for your advice I really do appreciate this.

---

### Post by Jman1989 on 2008-04-17
I'm a BIIIIIIIG ubuntu newbie so I dunno if i messed up or what, but when i put that in it always says

"Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop"

What am do I need to do?

---

### Post by Jman1989 on 2008-04-17
ack i replied to my own post.. >.<

---

