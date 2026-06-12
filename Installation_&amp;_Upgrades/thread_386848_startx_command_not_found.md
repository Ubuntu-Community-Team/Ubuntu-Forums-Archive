---
title: "startx :command not found?"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by cje on 2007-03-17
I've installed Ubuntu Server 6.1 and Ubuntu GUI. 
But, when I try to start the GUI interface with the sudo startx command I get the "command not found" error. 
Any idea what to do?

---

### Post by bulldog on 2007-03-17
You can try to start GDM ```
sudo /etc/init.d/gdm start
``` to see if the GUI is working.

How did you install the GUI ?```
sudo aptitude install ubuntu-desktop
```

---

### Post by cje on 2007-03-17
thanks for your quick reply.

I've tested the 
sudo /etc/init.d/gdm start 
and found that xserver was not installed!? I don't know why. 
Anyway, I'll try your command and return after re-installing.

---

### Post by kerry_s on 2007-03-17
sudo apt-get install xorg

---

### Post by cje on 2007-03-17
The re-install did work.
Anyway, I really don't understand why it didn't install the first time ....
Anyway, thanks for replies - hopefully it will be helpful for others too

---

