---
title: "Alternate text based installation blanks screen???"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by carlos123 on 2006-06-14
I have tried to install Ubuntu 6.06 to an external USB drive using the LiveCD graphical install to no avail.  It seems that it just can't be done that way.  

So...I downloaded and used the alternate CD with a text mode installer.  Things went more or less okay until the installer gets to a part where it is doing something without any activity appearing on the screen (configuring GNOME or something like that).  The screen goes blank except for two square cursor thingies that sit there about 3 inches apart.  Nothing I type on the keyboard brings back the screen.  Alt+F1, Alt+F3, no keys do anything to bring back the screen.  

I managed to finally get through the installation by just pressing Enter and letting the installer continue from wherever it was.  But I spent hours trying to install it over and over again.  

In other words keys still worked but I could not see where the intaller was in it's interface because the screen was blank except for those two cursor thingies.  

A server installation worked fine.  

This happened only through installation of the Desktop when it got to that part that took forever to do and that resulted in no activity on the screen.  

Normally I would think this is some kind of screen saver thingy activating but there is no BIOS related screen saver active.  Nor does the screen respond to keys being pressed.   I have not had this problem with the graphical installer (which fails for other reasons) or any other Linux anything.  

I now have a working Ubuntu on my USB drive but am wondering why this happens.  I don't want to ever install Ubuntu on some business computer and be stuck having to go through the same thing again.  

Any input on how to get around this problem or what could be causing this?  

I am running a Toshiba ML-70 DL3 laptop.  

Carlos

---

### Post by stlutz on 2006-06-15
When I installed Breezy, I had a problem with the x configuration and the screen went blank.  Everything seemed to install okay--I booted up in failsafe mode and ran "dpkg-reconfigure xserver-xorg" and chose the vesa graphics driver instead of.  Once I was able to get x going, I then intalled the nvidia modules and all was well.

---

### Post by sam81 on 2006-06-18
[QUOTE=carlos123] 

So...I downloaded and used the alternate CD with a text mode installer.  Things went more or less okay until the installer gets to a part where it is doing something without any activity appearing on the screen (configuring GNOME or something like that).  The screen goes blank except for two square cursor thingies that sit there about 3 inches apart.  Nothing I type on the keyboard brings back the screen.  Alt+F1, Alt+F3, no keys do anything to bring back the screen.  
Carlos[/QUOTE]

Hi, I had exactly the same problem yesterday on a Dell Inspiron 9400, during the installation of packages the screen went blank except for the two square cursor thingies. I have no idea why. The graphical installer works fine on this laptop (in safe graphics mode), and I already have dapper installed, but I would like to install another copy on a spare partition to try the new testing distribution (edgy), and I want to use the alternate cd to avoid overwriting grub in the MBR.

---

### Post by sam81 on 2006-06-19
I got around the problem following the advice given in another thread:

-from the alternate cd choose the server install, this will install the base system, and  some other packages needed to run a server

-when the installation is finished you won't get X, just the command line, type
sudo apt-get install ubuntu-desktop
to install the xserver, and the rest of the desktop environment.

Good luck!

---

### Post by rcarring on 2006-06-19
That's the method I would recommend on newer hardware / graphics cards. Doing a server install lets you get a base system working, then you can add the gui side (xserver etc). I do a server install then get xfce. Once I am in the light gui, I can install ubuntu-desktop  and switch to Gnome from the login screen.

---

