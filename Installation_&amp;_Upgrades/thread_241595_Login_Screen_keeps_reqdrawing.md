---
title: "Login Screen keeps reqdrawing"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by jazzfish on 2006-08-22
Greetings,

OK.. I upgraded my working and nicely configured Breezy to a now not-able-to-login Dapper.  It seems X is working as login screen looks fine. Problem is each time I enter a valid U/N P/W  combo it appears to be starting up the desktop, but returns again to the graphical login screen.

I tried running sudo dpkg -i xerver-xorg-core*.deb (after the wget) and that ran fine (from console window) but after rebooting no difference. 

I am using the Gnome desktop (I have a few K packages that I had installed.. don't know if thats a bad thing.. ) and like an earlier poster the /var/log/gdm says something about Glibcore not loading..  I recently tried to install real player which failed.. although I don't see how that could have caused this. 

Any ideas would be really appreciated!!

- Bob

---

### Post by linear on 2006-08-22
One possibility is incomplete upgrade due to dependency problems, so I'd recommend a look at this thread: [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656), and especially the troubleshooting steps in this thread: [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672).

---

