---
title: "Daily Build 20081014 boot black screen on Thinkpad"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-10-14
Ubuntu Daily Build 20081014 CD Live Intrepid Beta still fails.  Boots to black screen where Gnome desktop should load.  

IBM Thinkpad R31 32 bit Celeron, Intel graphics is hung altogether except for power off key.  Launchpad bug 277344.  

Alpha 5 NOT UPDATED, hardy, gutsy, feisty, edgy, dapper all run O.K., but not! Alpha 6 or Beta.  Well, Xubuntu & Kubuntu Beta run O.K.

Found a workaround:
Boot CD Live 
Watch for X to initialize
Ctrl-Alt-F1    (timing dependent, might have to do it a few times)
At command line prompt:
sudo killall gdm
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo startx

and away it goes, booting successfully, gnome desktop and all!
Well, not quite all - switcher fails, reload? select don't reload, to get switcher functions just do Alt-F2 and enter the command, sudo halt or sudo reboot or sudo whatever.

Sure could use a CD Live boot option to remove compiz!!  Since I do a lot of full screen applications like Internet, Office, Picasa, ... I do System Preferences Appearance Visual Effects None anyway, if Ubuntu is able to boot without black screen freeze.

Jerry

---

