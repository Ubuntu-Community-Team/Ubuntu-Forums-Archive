---
title: "Not detecing Wireless USB?"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by chumpchous on 2004-10-25
nevermind! success. Ndiswrapper -l shows 
wusb54gv2 driver present, hardware present

So I should be good to go, just a matter of installing everything. Sorry for spamming up the forums. 

If anyone else is having problems installing this device, I needed to use the wusb54gv2.inf AND have wusb8xp.sys (or something like that, I cant remember) together in the same directory before running ndiswrapper -i wusb54gv2.inf.

---

### Post by olivierD on 2004-10-26
[QUOTE=chumpchous]nevermind! success. Ndiswrapper -l shows 
wusb54gv2 driver present, hardware present

So I should be good to go, just a matter of installing everything. Sorry for spamming up the forums. 

If anyone else is having problems installing this device, I needed to use the wusb54gv2.inf AND have wusb8xp.sys (or something like that, I cant remember) together in the same directory before running ndiswrapper -i wusb54gv2.inf.[/QUOTE]

did you make :
root# modprobe ndiswrapper

if you have some errors try to edit /boot/grub/menu.lst and replace acpi=on by acpi=force, it works for me for my gericom laptop and wireless pcmcia card

bye

---

