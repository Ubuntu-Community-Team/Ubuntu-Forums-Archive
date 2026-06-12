---
title: "Lost ability to change screen resolution in KDE"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by frkstein on 2007-02-28
I just upgraded from Breezy to Dapper. Now, when I login in to KDE, I cannot find how to adjust my screen resolution. It has me stuck at what I think is 1024x768. The resolution I want is 1440x900. If I log in to gnome, it will let me adjust to the resolution I desire. To clarify, under breezy I used to be able to right click on the desktop to bring up a menu. Under that menu I could select configure Desktop. I would then be offered as one of my options 'Screen Settings'. Here is where I could change the screen resolution. Can someone please offer some suggestions?

---

### Post by frkstein on 2007-03-05
Just posting this as a follow up. I solved the issue.

You need to edit /usr/share/applications/kde/display.desktop

You need to comment out the following line:

noDiplsay=true

---

