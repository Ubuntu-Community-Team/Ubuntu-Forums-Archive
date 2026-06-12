---
title: "Drive management"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2006-11-29
I upgraded from 6.06 to 6.10 and I noticed in the system>admin menu that the 'drives'(think I remember the correctly) program is no longer there.  Is there an alternate GUI for mounting and unmounting hard drives?

---

### Post by lhtown on 2006-11-29
Maybe 'System Monitor' is what you are looking for under System > Administration.

Also, there is always the reliable /etc/fstab 

Perhaps there is another option, but I don't know.

Is your hard drive internal or external and how does it connect?

---

### Post by Deadheded on 2006-11-30
In 6.06 it was System>Admin>Disks the title bar was "Disks Manager"  the launcher command was gksu disks-admin but that does not work in 6.1..  this is an internal drive IDE...

---

### Post by Robert.Zapata on 2006-12-13
Check **pysdm** *(is on Synaptic).*


[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

and also **gparted** *(also in Synaptic)*

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

Is the replacement for **"Disks Manager"**

---

