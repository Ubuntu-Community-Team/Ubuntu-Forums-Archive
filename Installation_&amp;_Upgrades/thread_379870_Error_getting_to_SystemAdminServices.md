---
title: "Error getting to System/Admin/Services"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by ebike on 2007-03-08
Hi All,

I have just become a Ubuntu convert from Gentoo. I have installed Edgy on
a Dell 500m Inspiron and eveything is mostly ok except for a couple of issues.

1. The main problem is I get an error trying to get to the menu item System->Administration->Services. I get the error:

> "The configuration could not be loaded, You are not allowed to access the System Configuration"

It used to work, but now it doesn't.  ... and yes I was asked for the root password, and it was accepted.

2. Trying to get printing to work on my print server. I have an edimax print server that I used to be able to print to using IPP protocol with gentoo. The device settings in the print manager is "http://192.168.0.170:631/lpt1", but it doesn't work. Maybe cupsd.conf needs changing for Ubuntu?

3. I have managed to get a wlan0 wifi device working with driverloader, but I don't see that interface with ifconfig.

Hope someone can help. Thanks.

---

### Post by Kateikyoushi on 2007-03-09
For the first problem run "alacarte" menu editor from the terminal then go to >System >Administration.
Add gksu to the beginning of the command ie. gksu services.

---

### Post by ebike on 2007-03-09
I checked that, and the menu items had gksu in front of them allready. I have found the solution to that problem in another thread. I had to re-install dbus + gnome-system-tools + system-tools-backend ... that fixed it. Maybe I had accidentially un-ticked the dbus service in that menu ..

---

### Post by ebike on 2007-03-09
The dbus issue fixed the printing issue, so that is fixed.
All I need now is an answer to the wifi issue ....

---

