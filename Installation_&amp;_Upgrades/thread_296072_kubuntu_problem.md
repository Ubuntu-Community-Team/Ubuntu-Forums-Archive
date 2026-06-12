---
title: "kubuntu problem"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Orion2000za on 2006-11-09
I have a strange problem running Kubuntu Edgy;
I don't need the kdebluetooth package since I don't have bluetooth. Trying to uninstall packade and some others like desktop sharing always includes removing kubuntu-desktop. 
And if I do that several panels in System Settings such as Monitor, Disk & file systems etc disappear. 

any ideas, I need bluetooth as much as I need headache.

Sinclair

---

### Post by an.echte.trilingue on 2006-11-09
That should not happen since kubuntu-desktop is a meta package, meaning that it does not contain any actual binaries or config files, it just depends on all of the elements of the kubuntu desktop.  Try to uninstall just kubuntu-desktop by itself and see what happens.  I think you problem is elsewhere.

---

### Post by Orion2000za on 2006-11-09
Well it did happen ;) but your solution worked! Thanx.

Sinclair

---

### Post by an.echte.trilingue on 2006-11-09
Well, what I meant is that you probably uninstalled something else by accident when you uninstalled kde-desktop.

---

### Post by Orion2000za on 2006-11-09
I see what you mean BUT the desktop insisted on being uninstalled together with eg kdebluetooth. No other packages indicated whether I did this via Adept or apt-get. Still the whole guidance seemed to disappear. 

SOLVED for now however

---

