---
title: "Need advice on installing ATI driver"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by jfreelix on 2008-08-24
I have a laptop with a 16Mb Radeon mobility (M6?) graphics chip and I can't find or install the appropriate driver. I want to use the desktop effects and view various programs in 3D but it says I can't because it says there is no driver installed. I am new to Linux and Ubuntu so I do need a bit hand holding. I followed some directions I found in the forum...there was something about entering some lines I think in the terminal but that didn't work. I'm sure everything is user error so somebody please fix me. I have installed the latest version of Ubuntu within Windows XP so my system works as a dual boot system.

---

### Post by Pumalite on 2008-08-24
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Catalyst2Death on 2008-08-24
Do you mean that you used the Wubi install?  This could change some things.  Otherwise, I'm pretty sure that the proprietary drivers from the Hardware Drivers menu should allow compositing.  Failing this, the radeon drivers should also support direct rendering for you card.  So, via hardware drivers:

System>Administration>Hardware Drivers  then check enable, it will download and prompt restart.  Do this.

To do the radeon drivers:

```
sudo cp /etc/X11/xorg.conf{,bak} # Creates a backup named xorg.confbak
sudo nano /etc/X11/xorg.conf
```

find the Device section,
look for Driver and edit "ati" to read "radeon"
restart, X11 fails to start, then you'll be dropped into a command line, then do this:

```
sudo cp /etc/X11/xorg.confbak /etc/X11/xorg.conf
```

then restart again, and stuff will be back to normal.  If you insist on using the latest proprietary drivers check here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

it has more detailed instructions regarding what I've outlined above, so read it anyway.  Also, the terminal can be found via Applications>Accessories>Terminal  I should suggest binding it to a shortcut key so that you can access it quickly:
System>Preferences>Keyboard Shortcuts (find Run a Terminal)

---

### Post by jfreelix on 2008-08-24
I have checked in the hardware drivers and it says that "no proprietary drivers are  in use on this system."

---

