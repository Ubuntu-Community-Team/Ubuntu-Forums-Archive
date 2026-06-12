---
title: "upgrade from xubuntu 13.10 to 14.04. Lightdm fails to start"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by Mishkin-Rayman on 2014-04-24
Upgraded from xubuntu 13.10 to 14.04. After upgrade, I'm logged directly into terminal. No graphical interface.

After a bit of web searching, I tried giving the command sudo service lightdm start, terminal replies "Job failed to start".

I'm not that good with Ubuntu, so I don't know what to do next. This is a f***ing nightmare since It's my work laptop and I really need it to work. How do I get into graphical interface??!!! :mad:

---

### Post by Mishkin-Rayman on 2014-04-24
startx doesn't work. 

> modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='fglrx'
modprobe: ERROR: could not insert 'fglrx': Function not implemented
(WW) fglrx: No matching device section for instance (BusID PCI:0@1:0:0) found
(WW) fglrx: No matching device section for instance (BusID PCI:0@0:1:1) found
modprobe: ERROR: ,,/libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='fglrx'
modprobe: ERROR: could not insert 'fglrx': Function not implemented
(EE)
Fatal server error:
(EE) no screens found (EE)
(EE)
[--]
xinit: giving up
xinit: unable to connect to X server: Connection refuser
xinit: Server error

Tried sudo apt-get install fglrx. It installed. 

Rebooted and retried to run startx. Yields the same response.


Trying to run a graphical program from terminal such as mousepad or gedit yields reply [B]"gtk-WARNING **: Cannot open display

Suggestions, anyone?[/B]

---

### Post by Mishkin-Rayman on 2014-04-24
This is the LAST ****ing time I'll EVER upgrade my OS. 

Going ahead to rip the harddrive out of my laptop, backing my files up and re-installing from scratch. 

mother****er. ARRGH!!

---

