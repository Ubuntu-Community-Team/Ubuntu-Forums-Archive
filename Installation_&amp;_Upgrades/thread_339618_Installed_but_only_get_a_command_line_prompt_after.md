---
title: "Installed but only get a command line prompt after boot"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by dlynch13 on 2007-01-16
Hi,

I am trying Kubutu desktop out and my CDROM drive is flaky so I found an installed the mini.iso image, which then went out and fetched necessary files from the web during install.  This worked fine.  When it rebooted after install, it booted to a command line only.  How do I start the GUI?  Will it be possible to make this machine a normal graphical desktop machine or do I have to start over?

Thanks, David.

---

### Post by Sef on 2007-01-16
To get a GUI, just use the code below:

```
sudo aptitude install kubuntu-desktop
```

---

### Post by aysiu on 2007-01-16
Sef is right on.

I would add that you might want to do just a little more: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm restart
```

---

### Post by dlynch13 on 2007-01-16
OK, so the first thing from Sef worked and I got on the Kubuntu desktop last night.  (Thanks!) I tried to install Firefox but I didn't know what to do with a .gz file.  So then I found the installer that is built into the menu system.  However, once installed, I didn't see Firefox anywhere in the menus.  After I rebooted, everytime that I try to login, I get the stopwatch and then it kicks me out to the login prompt again.  I am locked out.  There are no error messages.  How do I recover from that?  Note that I can still do stuff from a terminal in the other windows (Ctrl+Alt+F3 for example.)  I just can't get into the GUI.

Thanks, David.

---

