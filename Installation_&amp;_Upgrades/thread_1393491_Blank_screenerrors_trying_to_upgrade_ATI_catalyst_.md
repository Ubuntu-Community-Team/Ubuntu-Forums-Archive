---
title: "Blank screen/errors trying to upgrade ATI catalyst drivers"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by ManiacDan on 2010-01-29
So xorg was acting up, and I went into the Hardware Drivers menu to see if the driver had a problem.  The driver was disabled, and could not be activated.  I downloaded the new ATI driver.  I uninstalled the old one, installed the new one, and ran the config step just like it specifies in the install instructions.  Upon reboot, I got a blank screen instead of the login screen.

I managed to drop back to the command line and uninstall the driver, so now I'm stuck in ubuntu with one monitor instead of 2.  

I tried to re-activate the driver and got the message "/etc/X11/xorg.conf is invalid"

This worried me, so I tried to rebuild xorg.conf, which does NOTHING:
```
root@my-desktop:/etc/X11# rm /etc/X11/xorg.conf
root@my-desktop:/etc/X11# dpkg-reconfigure xserver-xorg
root@my-desktop:/etc/X11# ls -al /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory
```I have a backup of my old xorg.conf, but it expects the ATI driver to be installed, which clearly doesn't work.

I'm going to *attempt* to revert to the old ATI driver (which I still have in my home dir), but I wanted to be sure to get this into the forums before I ruined my GUI again.

Any thoughts?  I can post the xorg.conf files that I have if anyone thinks that will help.

-Dan

---

### Post by ManiacDan on 2010-01-29
Update:  I restored an old backup of xorg.conf and installed envy.  I went through the uninstall/reboot/install/reboot path for envy and got the error:
> Missing PCS Default File /etc/ati/ampdpcsdb.defaultThere is a file called ampdpcsdb in that directory, but when I copy it into the -default position I get a screen overlay that says "ATI TECHNOLOGIES - FOR TESTING PURPOSES ONLY - UNSUPPORTED HARDWARE" and still nothing works.

Before anyone asks, buying an nvidia card isn't an option, this is my work machine.

-Dan

---

### Post by ManiacDan on 2010-01-29
Using Envy to uninstall everything, manually wiping out xorg.conf, then installing version 9.10 and manually running "aticonfig --initial -f" fixed it.

Well, "fixed it" in that now I can operate my machine again, but I'm still running a year-old version of the display driver that breaks a few things and causes X to randomly freeze, but it's better than a punch in the face.

Leaving this thread unsolved in case anyone stumbles upon it and can offer a solution.

-Dan

---

