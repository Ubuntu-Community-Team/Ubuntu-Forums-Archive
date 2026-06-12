---
title: "many issues while upgrading to gutsy."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by PanzerMKZ on 2007-12-19
I have upgraded to Gutsy.  now I am getting a few issues.


First of is I am unable to install apcid now.  

get errors were encountered while processing:
acpid
acpi-support
powermanagement-interface
xfonts-scalable


also when I do a startx I get 
error in locking authority file /home/home/.Xauthority
/etc/X11/X is not executable


TIA
Panzer

---

### Post by PanzerMKZ on 2007-12-19
ok was able to get the acpi stuff taking care of by stopping the acpid

sudo /etc/init.d/acpi stop

then running 

sudo dpkg --configure -a


But now I still have those other issues.


Panzer

---

