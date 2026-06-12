---
title: "Need to reconfigure me graphics after moving HD to new machine."
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by carl99fan on 2009-12-22
How do I do this?
There are nvidia drivers on here from my old machine. I am running Karmic.
Now I have an Intel graphics on board.

---

### Post by lemming465 on 2009-12-24
Boot to a command prompt login (if you can't get there by Ctrl-Alt-F2 from a regular boot, try a "recovery" boot to single user mode, or edit the grub boot kernel line).
Login in with your regular user account, and try "sudo dpkg-reconfigure xserver-xorg".

---

