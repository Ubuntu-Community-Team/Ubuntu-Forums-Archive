---
title: "Update broke X"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by schmolch on 2009-10-10
Afer some updates a few hours ago X wont start anymore.
I log in via gdm and it tries to start X only to return to gdm.
I found this errors in .xsession-errors:

XIO: fatal IO error 104 on X server ":0.0" after 6 requests...
followed by the same msg from all the apps that use to autostart:
gnome-session: Fatal IO error 104 on X server :0.0
gnome-settings-daemon: Fatal IO error 104 on X server :0.0
....

Im using a all intel thinkpad with intel gma 950 gpu.

---

### Post by schmolch on 2009-10-10
update: startx still works
i guess its something with gdm.

---

### Post by emarkay on 2009-10-10
Wonder if it's the same thing here:[http://ubuntuforums.org/showthread.php?t=1287628](http://ubuntuforums.org/showthread.php?t=1287628)

I didn't see any errors, though.

---

