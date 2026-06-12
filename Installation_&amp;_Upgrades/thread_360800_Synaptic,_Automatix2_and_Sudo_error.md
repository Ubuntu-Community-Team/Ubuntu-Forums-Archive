---
title: "Synaptic, Automatix2 and Sudo error"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Noodle1989 on 2007-02-13
Well when I try to install anything from either Synaptic, automatix2 and Sudo I get this message.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " 

How do I exactly fix this? as I type dpkg --configure -a into the terminal but don't know where to go from there. Could someone please lead me in the right direction

Thanks in advance, Noodle

---

### Post by Jussi Kukkonen on 2007-02-13
prefix the command with *sudo*, then it should work. Like so:
```
sudo dpkg --configure -a
```

---

