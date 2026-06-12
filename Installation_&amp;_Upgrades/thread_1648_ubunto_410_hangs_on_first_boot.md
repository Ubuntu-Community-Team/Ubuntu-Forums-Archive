---
title: "ubunto 410 hangs on first boot"
date: 2004-10-22
forum: Installation &amp; Upgrades
---

### Post by giorsat on 2004-10-22
Hi. I tried ubuntu final on a lcd computer with sis motherboard, sis video, sis audio.
Installation goes fine with noapic nolapic acpi=off nopcmcia (the right lcommand is on F8 help tips) . At first boot even with noapic nolapic acpi=off ths system hangs when hotplug starts sayin
MODPROBE FATAL error inserting pciehp. operation not permited
MODPROBE FATAL error inserting shpchp operation not permited
nothing to be done except plug it off.

the computer works perfectly with mandrake 10 and 101. please any help or idea is welcomed. I'ld like so much to change mandrake with debian ubuntu
gio

---

### Post by j_baer on 2004-10-22
I am experiecing the same problem.

   Abit AT7 motherboard,
   AMD 2100 cpu,
   nVidia TI-4400 video

   HP USB Deskjet 5650 printer

Likewise, this computer has successfully run SuSE and Fedora ...

---

### Post by haha on 2004-10-22
I had same problem, too

first, unplug USB device before booting.

---

### Post by j_baer on 2004-10-23
All,

I re-installed Ubuntu from an ISO dated 10.20.04. The problem did not go away, but the system did no hang.

I also took a guick look at rc-2. As best as I can tell it booted without error.

---

### Post by mdetreville on 2004-11-05
I have the same issue with a Toshiba Tecra 8300 after the reboot part way through the installation. There are no USB devices attached. Which of the modules can be eliminated using the 'expert' installation method to ignore USB entirely?

---

### Post by ctof on 2004-12-22
i have the same pb,
is there a solution/workaround to successfully boot (why not without usb support 0 ?
Thx
Christophe

---

### Post by mirexastan on 2004-12-22
Guess that's why most of us is here in the same forum. Just tried 410 and after the 
initial install, it hangs when loading grub. Blinker just blink, blink, blink. Will try pulling 
out the usb keyboard and mouse to try again as suggested by someone here...
Hopefully by the time I post back, things will be better.

---

### Post by ctof on 2004-12-22
Excuse me 

i'm not sure to get you
what do you mean by 410 ? if it is the warty release, i already us this version.
another thing is i have no usb device (or maybe the 3inI card reader. CF,SD but this hardware is bundle/integrate ?  in my computer.

---

