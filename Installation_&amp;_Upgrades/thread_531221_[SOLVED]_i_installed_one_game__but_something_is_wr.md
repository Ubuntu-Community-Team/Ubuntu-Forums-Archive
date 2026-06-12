---
title: "[SOLVED] i installed one game  but something is wrong"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by cc93 on 2007-08-21
hi i have just installed a game called  assaultcube    from here: [http://assault.cubers.net/](http://assault.cubers.net/)
but i can't find it  in : MENU: applications>games :(:(
can you help?

---

### Post by adewale on 2007-08-21
was it a deb you downloaded ? if so open synaptics and search for it, also since its a game, it should install to your home folder, look for the game launcher and then right click your menu and choose edit menu and create a new menu item under game and point it to your game launcher

---

### Post by cc93 on 2007-08-21
i found it in synaptic but i can't find it in my home folder

:confused::(:confused:

---

### Post by maybeway36 on 2007-08-21
Try looking in /usr/bin

---

### Post by cc93 on 2007-08-21
i still can't find it
can i use some how the synaptic?

---

### Post by maybeway36 on 2007-08-21
I think with synaptic you can get a list of files that belong to each package. I know with Adept you can.

---

### Post by cc93 on 2007-08-22
i found it in adept. now how can i play it or add it in my menu ??

---

### Post by Outrunner on 2007-08-22
```
assaultcube
```

Try typing that in the terminal.

---

### Post by cc93 on 2007-08-22
commant not found  :(

---

### Post by cc93 on 2007-08-22
if i make it reinstall it might be fixed?

---

### Post by meindian523 on 2007-11-17
try ```
apropos assault-cube
``` in terminal

edit:wrong command,changed.....

In Synaptic,you can search for Assault Cube and when you find it,select it,click on Package-->Properties-->Installed Files.

Look for files in /usr/bin or /usr/sbin ......

---

### Post by cc93 on 2007-11-17
thx man it worked :popcorn:

---

### Post by meindian523 on 2007-11-17
what worked???

Please explain and thence mark thread as solved....

Thread tools-->Mark as Solved.

---

