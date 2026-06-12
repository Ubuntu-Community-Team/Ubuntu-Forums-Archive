---
title: "Ubuntu linux 18.04 freezes randomly after updates"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by daveads on 2018-10-21
after installing the linux distro........... i did an update && upgrade and also installed LXDE desktop Environment
but before this ubuntu work fine no random freezes...... 
//the problem still persist in the lxde desktop environment so it's not the desktop environment
need help..........
Thanks in advance!!

---

### Post by dino99 on 2018-10-21
What was your primary DE ?  gnome-shell ?
So if your system have 2 DEs, then dont be surprised to get some conflicts.

To know what is going on, run 'journalctl -b' for actual session, or 'journalctl -b -1' for the previous one.

---

### Post by daveads on 2018-10-21
i don't its the desktop environment that is causing the problem 
am use an lxde nd gnome // the other is light weighted so am not sure if that is the cause 

i use the command journalctl -b -1  i guess i will ve to wait for another freeze to happen 
so i can try the command again

---

### Post by daveads on 2018-10-21
i just had the freeze....
what was i suppose to watch out for @ the command journalctl -b -1

---

