---
title: "upgraded 6.06 to 6.10 now gnome broken"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by herot on 2006-12-20
i did exactly as the official ubuntu upgrade readme said...

it upgraded my system... asked if i wanted to skip removing some stuff... i let it remove them...(like 20+ items i think)...

anyway it boots but all i get is a desktop... with all my old icons on it... i have no menu bar or active app bar or anything... had to go through my computer and find the firefox in /usr/bin to type this!

funny thing... i can run Neverwinter Nights just fine! (and whatever else has an icon on the desktop...)(i guess at least GL is working... and wireless...)

and yes i used the official method to upgrade...

please help!

---

### Post by invalid on 2006-12-20
Try```
killall gnome-panel && gnome-panel &
```

---

### Post by herot on 2006-12-21
it said no 'no process killed'

what now? i guess the genome-panel isnt getting started?

*update* ok i am able to start the panel as long as i execute "gnome-panel &" on a terminal inside genome (which i have to go through /usr/bin/x-terminal-emulator to get to)

why isn't it starting when gnome starts?

---

### Post by herot on 2006-12-21
anyone?

---

### Post by herot on 2006-12-21
help!

---

### Post by herot on 2006-12-21
and also when i try to make my fonts larger on the menu bar... i get this message

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

PS actually... the message appears no matter which item in preferences i choose...

something got broken but i dont know what or how to fix it...

---

### Post by BLTicklemonster on 2006-12-21
can you right click on the desktop and click 

create launcher

and make a new launcher with stuff you can use?

Utilities: Main Menu would get you back to applications and all if you can do that. In the meantime, that is, until you get everything sorted out.


oooor, in syanaptic, remove gnome-panel and gnome-settings-daemon, then install them (or actually, just attempt to reinstall them first)

---

### Post by herot on 2006-12-21
i got this...

root@Armagh:/home/herot# apt-get install gnome-settings-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-settings-daemon
root@Armagh:/home/herot#

---

