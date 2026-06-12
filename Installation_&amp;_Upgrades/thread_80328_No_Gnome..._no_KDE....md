---
title: "No Gnome... no KDE..."
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by Mr.Clark on 2005-10-21
Um. I *think* I just installed Breezy. The live disc works fine. However, on the install, getting past the Username/Password problems (it never asked me for a Root password, for one thing), on boot up, the network card takes so long to load ("Waiting for network interface to come up") that the GUI fails and I end up with a terminal prompt asking me to log in. If I do, it looks like a regular terminal shell, but no sign of Gnome or KDE. Just text :shock:

Any ideas? Every time I try and install, something cocks up. Mostly GRUB, but since that is in the MBR and working, I wouldn't have thought not installing again makes much difference.

Thanks in advance folks...

---

### Post by aysiu on 2005-10-22
Two things: 

1. After you log in, what happens when you type in ```
startx
```?

2. What happens if, instead of logging in, you press control-alt-F7?

---

### Post by Mr.Clark on 2005-10-22
[QUOTE=aysiu]Two things: 

1. After you log in, what happens when you type in ```
startx
```?[/QUOTE]```
-bash: startx: command not found
```
Same with "sudo startx"

[QUOTE=aysiu]2. What happens if, instead of logging in, you press control-alt-F7?[/QUOTE]Nothing.

*sigh*

Reinstall, here I come. Change network cards first, methinks...:(

---

