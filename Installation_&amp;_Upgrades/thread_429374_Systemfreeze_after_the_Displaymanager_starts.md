---
title: "Systemfreeze after the Displaymanager starts"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by agentorange on 2007-05-01
Hi,
 i'm trying to use ubuntu on my system, but everytime it starts (either during the livecdsetup or after a textbased install) the system freezes completly a few seconds after the displaymanager has been started (can't move mouse or hit ctrl+alt+x). In the first few seconds i can move the mouse
what works is starting in rescue mode and execute startx as root. The Xorg logfile doesnt display an error message. I also tried passing nolapic or noacpi to the kernel as boot parameters, which didn't change anything either. Is there something else i might try?
Thanks for your advice

Just for you information i'm using:
- Ubuntu 7.04
- Geforce 6800 GT
- Athlon 64 3200

---

### Post by agentorange on 2007-05-01
I just found out that the problem is unrelated to X, because in normal mode the system freezes even though i disabled gdm....

---

### Post by agentorange on 2007-05-01
OK, it seems to be powernowd which is causing the problems. i'm disabling it for now.

---

### Post by agentorange on 2007-05-02
It seems my system still crashes. But this time it takes always around 30 minutes and just happen out of a sudden. Can't find anything in the syslogs.

---

