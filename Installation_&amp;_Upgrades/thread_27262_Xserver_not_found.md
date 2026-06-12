---
title: "Xserver not found"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by mspilleb on 2005-04-15
Hi there,

I'm pretty new to linux, but amazed by the free ubuntu version.
I installed ubuntu on dual-boot machine (with windows XP) without any problems, but when I started Ubuntu, the desktop would not load. 
This is the error message I got:
---------
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth
/var/lib/gdm/: 0.X auth -nolisten tcp vt7
Error: command could not be executed!
Please install Xserver or edit /etc/gdm/gdm.conf to point to the right place
---------

somebody there to help me?

thx,
 Marijn

---

### Post by p!=f on 2005-04-15
Hi and welcome on the forums,

try to run this command 
```

sudo apt-get install x-window-system

```
Any changes?

---

### Post by mspilleb on 2005-04-15
wonderful!

I'm inside an wonderful desktop

thx a lot

 marijn

---

