---
title: "install hangs on loading usb.rc"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by Noremacam on 2005-11-28
I booted from the ubuntu 5.10 cd and hit enter for the default install. It seems fine, until it gets to the point where it runs "usb.rc", after which it just hangs. Perhaps I'm not waiting long enough? I waited for quite a while.

I've installed ubuntu on other computers before with no problem. I can't figure out why it's not working here.

The only thing I have on usb right now is the wireless mouse/keyboard combo.

The computer is a compaq presario with sempron processor, and 256 mb ram. Any help would be appreciated.

---

### Post by javapda on 2005-11-29
Same behavior here with...system hangs on /etc/hotplug/usb.rc

[LIST]
[*]Manufacturer: Frys Computer
[*]Model: 8140:Model
[*]Motherboard: RS480-M
[*]Mem: 2G
[*]Drive:  SATA - 250G
[/LIST]

---

### Post by bwog on 2005-11-29
Some of these laptops need special bootparameters for installation. I havent got a laptop, but you can try searching the forum for the name of your laptop (and/or bootparameters).

There is also some info here: [https://wiki.ubuntu.com/HardwareSupportMachinesLaptops?highlight=%28hardwaresupport%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops?highlight=%28hardwaresupport%29)

here [http://www.linux-laptop.net/](http://www.linux-laptop.net/) and here [http://www.linuxcompatible.org/compatibility.html](http://www.linuxcompatible.org/compatibility.html)

and there is a general HardwareSupport section in the wiki.

Sometimes you get very detailed install info in these sites, much of it is old though.

---

### Post by JKBurton on 2006-01-19
Mine worked with specifying:
     linux noapic nolapic
at the "Boot:" prompt.

Good luck!
Keith

---

