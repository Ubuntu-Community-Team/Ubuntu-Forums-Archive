---
title: "VIA chrome9 HC VGA"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by monsterstack on 2009-02-12
As the 8.10 live disc completely fails with this vga device, it's nice to see the infamous chrome9 vga working out of the box for Jaunty: complete with working resolution detection and default modes. glxinfo for me is a very definite yes on alpha 4. Jaunty also detects my laptop's battery properly, something only elive was able to do before.

It looks like compiz is being a bit dodgy at the moment according to other threads here, but I've never been able to use it in any usable fashion at all, even with VIA's own Ubuntu drivers. Does anyone know what's going on with openchrome? I don't know where to find information about this.

Are wobbly windows finally going to be a feature I can use? I do hope so.

---

### Post by drinky76 on 2009-03-08
I'm using Jaunty alpha 5 on an HP Mininote 2133 with the Via Chrome9 HC and I get the openchrome driver out of the box. Take a look in /var/log/Xorg.0.log to see which driver X is using.

I've not tried either the proprietary or open source drivers from Via for the Chrome9 yet as they appear to be for 8.10, still in beta (open source) and alpha (proprietary) and give you a choice between either working video playback or working 3D effects. The proprietary drivers have security issues and the open source ones are the same with some features removed according to the openchrome website.

Useful links if you're using the Mininote 2133:

[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133) and
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133/DisplayConfig810](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133/DisplayConfig810)
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
[http://www.hp2133guide.com/forums/viewtopic.php?t=1136](http://www.hp2133guide.com/forums/viewtopic.php?t=1136)
[http://forums.mininoteuser.com/viewtopic.php?f=11&t=666&start=0](http://forums.mininoteuser.com/viewtopic.php?f=11&t=666&start=0)
[http://www.openchrome.org/](http://www.openchrome.org/)

At the moment, I'll settle for the openchrome driver though it seems to offer no additional features beyond basic 2D acceleration.

---

