---
title: "custom install of Xubuntu 6.06"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by circ on 2006-06-05
I'm planning on installing Xubuntu 6.06. However, I'm not interested in the standard desktop install with OO, Ekiga and Gaim etc, but would rather set up a fairly barebones XFCE desktop with Firefox and something.

This was easy with FC5, where you just picked the packages you wanted during install, but when I later tried Ubuntu Dapper Beta 2 (I think), it just went ahead and installed everything without allowing any kind of package customization. After the install I tried to uninstall Ekiga, OO and Gaim, along with some other things with Aptitude, whereupon it informed me that it would have to uninstall some GNOME dependencies also, thus breaking GNOME.

Reading up on the net I noticed that the 'alternate' install might be able to do this, although I'm not sure as the topic wasn't discussed very comprehensively, or atleast that I saw. Would I have to do an OEM install, and then fill in the blanks once I reboot to get a system I want, or is there an easier way to customize it, or is this even possible? If OEM is the only way to do it, how difficult is this install compared to the standard text mode install?

---

### Post by Chickenmonger on 2006-06-05
The OEM install throws a normal K/X/Ubuntu install onto the computer, and allows you to log on as an OEM user to make final tweaks like adding proprietary drivers and programs. Then you run a special oem preparation command, and on the next reboot, K/X/Ubuntu will ask the user for a new username and password.

If you're looking for super customization, you actually might be better off with trying Debian Unstable, as opposed to Xubuntu.

---

### Post by ubnoobie on 2006-06-05
xubuntu doesn't use openoffice in it's default installation. it's main apps are: abiword, gnumeric, firefox, thunderbird, gaim, evince, thunar (file manager), mousepad (text editor) and xfburn.

if you want to do a 'clean' install and then pick 'n choose your packages. use the 'alternate' install cd and do a "server" install from it. this installs the standard base system only, no desktop (not to be confused with the server iso install cd, which also includes the server-optimised kernel). 

from there you can use aptitude to install the packages you want (and enabling the extra repos first if you want). the various *desktop meta packages are listed in aptitude (under tasks) so you can see what each of them includes.

at a minimum, you'd probably want x-window-system-core, xfce4 (this 'generic' meta package is in universe) and a display manager like gdm (or xdm, wdm)...

---

### Post by circ on 2006-06-05
Great, thanks.

---

### Post by ubnoobie on 2006-06-05
note if you install: x-window-system-core, gdm and xfce4, you might find that gdm's default session is gnome; as gdm's depends includes enough of a bare gnome install to load it. just change the option in gdm to default to xfce4 instead.

---

