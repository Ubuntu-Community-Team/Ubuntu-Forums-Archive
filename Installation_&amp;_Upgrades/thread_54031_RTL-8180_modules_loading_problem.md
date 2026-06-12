---
title: "RTL-8180 modules loading problem"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by FaBi3ttO on 2005-08-03
Hi all,
I'm using a Netgear MA521 which is based the Realtek rtl-8180 chip.
I don't use the ndiswrapper method because I've found a good open-source linux driver for my card.
The problem is: with the driver there are also a couple of modules which have to be loaded in the kernel with an "insmod" command.
How can I execute the script which automatically loads this modules in memory at boot time?

Thanks

---

### Post by direwolf on 2006-02-09
System > Preferences > Sessions 
Click the "Startup programs tab" 
Add the script 

Alternatively, you could have the modules loaded by opening a terminal and doing a 
sudo nano /etc/modules (or gksudo gedit /etc/modules) and adding the desired modules in the correct order - then save the changes.

---

