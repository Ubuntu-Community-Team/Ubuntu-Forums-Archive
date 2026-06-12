---
title: "Deleting a module  PERMANTLY!"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by |Eric| on 2008-08-07
:mad:Ok here is my plea . yes a plea !

ok i was able to compile a module the Marvell 88SE6145 SATA controler driver (filename:  mv61xx.ko)

yes it loads ! it works ! its a marvell! 
s**t :-( the default driver pata_marvell.ko does NOT whant to leave the place i tried moving it phisicaly to another location on the HDD removing it manualy & running depmod 
tried removing any kind of indication...
BUT THE DAM MODULE STILL LOADS !!!!

ok tried removing any referece here in /lib/modules/.../drivers
it still binds to the controller 
i can manualy unload it with modprobe & replace it with mv61xx but it will reload & rebind to the controler as soon as i reboot :-( 

help ! i just dont know what else to do ...

---

### Post by |Eric| on 2008-08-09
bump

---

### Post by sisco311 on 2008-08-09
i don't know how to remove it, but you can 
blacklist it, in order to prevent it to load at boot time.
add the following line to the* /etc/modprobe.d/blacklist*
file:
> blacklist <*module-name>*

---

### Post by |Eric| on 2008-08-09
already blacklisted it & didnt work :-( 

realy i downt know what the hell is happening

---

### Post by sisco311 on 2008-08-09
it's not an elegant solution but try to add the *modprobe -r ... *command 
to the */etc/rc.local *file.

---

