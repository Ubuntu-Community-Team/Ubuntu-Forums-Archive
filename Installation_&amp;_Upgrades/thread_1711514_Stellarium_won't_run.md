---
title: "Stellarium won't run"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by jack111 on 2011-03-21
I tried installing very popular application among astronomers (Stellarium) from Ubuntu software center, on 2 computers. 

On either of them, after clicking on Stellarium icon nothing happens.

Do you have any idea how to resolve this problem? I really need this program and I'm also quite new to Ubuntu.

Thank you very much

---

### Post by daggerstab on 2011-03-21
If your computers are using ATI Radeon graphics cards, then you most probably have this bug:
[https://bugs.launchpad.net/stellarium/+bug/481669](https://bugs.launchpad.net/stellarium/+bug/481669)

Try opening a terminal ("Applications" -> "Accessories" -> "Terminal", or simply press Ctrl+Alt+T) and running the following command:
```
stellarium
```
And see what happens.

---

### Post by jack111 on 2011-03-21
Is this supposed to work?? It simply just doesn't run...

And yeah, I have ATI Radeon graphic card.

---

### Post by daggerstab on 2011-03-22
No, it's supposed to be an easy way to view Stellarium's run log and see if there are any error messages in it. What is the last line of Stellarium's output in the terminal? (You can copy text from the terminal with Ctrl+Shift+C instead of Ctrl+C.)

---

### Post by jack111 on 2011-03-22
This is the result:

Using default graphics system specified at build time:  raster 
QProcess: Destroyed while process is still running.
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/doma/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/doma/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/doma/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL" 
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.

---

### Post by daggerstab on 2011-03-22
So yes, it's the Radeon driver bug I mentioned before.

You can update to a fixed version by adding the XOrg Edgers Personal Package Archive (PPA) that contains an updated version. Just have in mind that the packages in that PPA are not supposed to be stable and that it may cause some problems when you are upgrading to the next version of Ubuntu. Read the description:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

**If you decide to do it**, you need to add the PPA to your software sources and then update the packages. You can use the following commands in a terminal:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```

**The other option** is to wait a month or so for the next version of Ubuntu - it will contain the fixed drivers.

---

