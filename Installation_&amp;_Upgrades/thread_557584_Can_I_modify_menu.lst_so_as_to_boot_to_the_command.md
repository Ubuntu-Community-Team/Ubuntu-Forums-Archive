---
title: "Can I modify menu.lst so as to boot to the commandline?"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Durito on 2007-09-22
For various uninteresting reasons, I want to have a full Ubuntu install, but would like the option to boot to the command line when I don't need a GUI. What's the best way to do this?
 
I'm running Edgy on a Thinkpad 600e.

---

### Post by Pumalite on 2007-09-22
Recovery Mode

---

### Post by reckless2k2 on 2007-09-22
you could always "kill" gdm and always start at the cli and then startx if you like

```
sudo chmod -x /etc/init.d/gdm
```

to enable it again if you don't like that 

```
sudo chmod +x /etc/init.d/gdm
```

---

### Post by Pumalite on 2007-09-22
That's another solution.

---

