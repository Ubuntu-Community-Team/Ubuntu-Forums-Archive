---
title: "Screen stuffed need major help!"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Mb0742 on 2008-02-20
Hey,

I installed nvidia drivers and reset my pc but now the settings are above that, capable of my monitor, so I get an out of range error. The max I can set my screen to is 1280*1024 60hz can someone please help me set everything back to that setup?

EDIT: I can't actually get into ubuntu but I can get into that console restore thing.

---

### Post by sisco311 on 2008-02-20
backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```open it with nano text editor:

```
sudo nano /etc/X11/xorg.conf
```in the "Screen" section delete the unsupported resolutions.
save your file and exit(Ctrl+o, Enter, Ctrl+x)

go back to you gui and restart the x(Ctrl+Alt F7, Ctrl+Alt Backspace)
or if the x server is not started type: startx

---

