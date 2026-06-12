---
title: "Major help."
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by Vulcan on 2005-11-08
During my upgrade from Hoary -> Breezy, my computer froze, so I had to restart my computer. Once I did, all it came up was a terminal screen, no graphical login screen. I am able to do this via a Live CD.

---

### Post by az on 2005-11-08
boot into recovery mode and run
apt-get -f install
and follow the instructions


If that does not help, try

dpkg-reconfigure xserver-xorg


Run 
init 2
to get into desktop mode from recovery mode.

---

### Post by Vulcan on 2005-11-08
When I when init 2, it syas that I must be a superuser. Also, none of the other commands work.

---

### Post by az on 2005-11-08
[QUOTE=Vulcan]When I when init 2, it syas that I must be a superuser. Also, none of the other commands work.[/QUOTE]

In recovery mode you are root.  You are not asked for a password.  How did you boot your machine?  (If you hit escape and pick recovery mode in the menu, you will see what I mean)

What error do you get when you try
apt-get -f install?

anyway, try running that with sudo if you cannot get into recovery mode.

---

