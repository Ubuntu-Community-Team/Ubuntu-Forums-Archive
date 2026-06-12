---
title: "Black Background after upgrade"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Dasien on 2010-02-09
I just upgraded to karmic and now my background is black and I can not change it. The back ground shows through the program panel when it is set to transparent. Sort of weird;)
I included a picture
Nick

---

### Post by mushwars on 2010-02-09
[s]did you try setting the background image again?[/s]
did you try reinstalling gnome-panel
you could try nautilus that is responsible for the background

dont forget to use the purge not remove or you wont remove the bad settings.

---

### Post by NightwishFan on 2010-02-09
This might be some sort of odd permissions problem or problem with the Gnome Settings Daemon.. I really do not know how to fix either. Did you mess with permissions by any chance?

---

### Post by Dasien on 2010-02-09
Could you guys help give me and give a little how to or terminal commands on how to reinstall gnome-panel. Nightwhishfan I don't think I messed with any of the permissions is there any way for me to check, to see if I did. 
Thanks for the help

---

### Post by mushwars on 2010-02-09
```
sudo apt-get purge gnome-panel
sudo apt-get install gnome-panel
```
do the same with nautilus.

---

