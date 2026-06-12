---
title: "Empty session on Gnome"
date: 2009-02-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by henrique on 2009-02-03
I have an up to date jaunty installation and, after logging into Gnome, the desktop is empty and I have no panels.

It seems that the package gnome-session lacks the file /usr/share/gnome/default.session which exists in intrepid.

How can this happen?

---

### Post by sdowney717 on 2009-02-03
Interesting.
I had a problem once with hardy where I lost all my panels. Turned out a config file was the problem. I was also getting  error messages when the desktop would try to load that mentioned the problems and I could get no help on the forums.

After trying to unsuccessfully fix this, I tried something radical. I moved my important files.
I then deleted everything in my home folder and on restart, ubuntu recreated all the panels and the desktop was back. 
So if you ever get stuck, apparently ubuntu can restore itself.

What was interesting was I would delete everything and then ubuntu would recreate missing files in my home directory in real time.

---

### Post by marmuta on 2009-02-03
I was actually looking for a way to disable gnome-panel not long a go and couldn't find /gnome/default.session then. Apparently it's not used anymore and everything moved to desktop files. From
[http://live.gnome.org/SessionManagement/NewGnomeSession](http://live.gnome.org/SessionManagement/NewGnomeSession)

> Startup is controlled by .desktop files. The session manager does not have any hardwired startup apps (except gconfd and dbus-daemon, which it needs for its own purposes). The "default session" is just a directory containing a small number of .desktop files to be autostarted.

In the end blocking the panel worked when I placed a changed desktop file in ~/.local/share/applications. So perhaps you have something in there that blocks the panel from loading?

---

