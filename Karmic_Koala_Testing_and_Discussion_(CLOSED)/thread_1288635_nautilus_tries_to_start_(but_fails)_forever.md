---
title: "nautilus tries to start (but fails) forever"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Whise on 2009-10-11
i just upgraded to karmic a few hours ago

everytime i boot i get this strange bug behavior

nautilus tries to start but fails this creates a loop resulting in a bunch of opening windows in the taskbar that close a few seconds after.

After a couple of minutes my taskbar is completly cluttered with this and my system is slowed down significantly


hope someone can help all i can do is open a console and killall nautilus a couple of times until i can break this loop (i guess that when nautilus closes due to an error it tries to resume itself

---

### Post by P4man on 2009-10-11
You probably disabled nautilus to paint the desktop (been there, done that :p)  Open gconf-editor and go apps -> nautilus -> preferences, check "show_desktop".

If you dont want that, set X-GNOME-AutoRestart=false in /usr/share/applications/nautilus.desktop.

---

### Post by Whise on 2009-10-11
thank you very much for your kick reply , i hope this gets fixed in the final release

---

