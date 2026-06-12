---
title: "Unable to find provider 'gnome-wm'"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by psb6m on 2008-11-08
I just installed Intrepid on a computer with an Intel graphics card and got the problem reported in this thread in the closed "Intrepid Ibex Testing and Discussion" section.

[http://ubuntuforums.org/showthread.php?t=940630&highlight=gnome-wm+black+screen](http://ubuntuforums.org/showthread.php?t=940630&highlight=gnome-wm+black+screen)

That is, the login screen appears as usual, but a session never does get started. The screen freezes before anything besides a monochrome background has appeared; the mouse pointer moves, but the system does not listen to the keyboard.

The suggested workaround is to uninstall compiz and compiz-core, but when I do that I get no Gnome at all: just a text-mode prompt. I've wondered if it would make a difference to turn off all Visual Effects, but of course I can't get as far as accessing that dialog box and have no idea where to find the appropriate configuration file.

.xsession-errors shows the error in the subject line, and gnome-wm.desktop times out while waiting to start.

This was reported as a bug before the release of Intrepid but I guess was never fixed. But has anyone encountering this bug actually managed to get Gnome working?

---

### Post by jpcote on 2008-11-22
I'm having the same problem, but I can't even really log in. When I do it loop back to the log screen after few seconds. Because nothing is loader, I can't do the ```
metacity --replace
```

Help
[French post at ubuntu-fr.org with some images](http://forum.ubuntu-fr.org/viewtopic.php?id=271941)

---

