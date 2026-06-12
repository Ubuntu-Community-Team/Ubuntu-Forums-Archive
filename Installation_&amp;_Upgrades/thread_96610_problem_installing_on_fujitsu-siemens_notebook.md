---
title: "problem installing on fujitsu-siemens notebook"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by serban83 on 2005-11-29
hello

i have a problem trying to install linux ubuntu 5.10 on a Fujitsu Siemens Amilo M1451G notebook.

the setup process goes fine, but after restart, booting stops at *starting hotplug subsystem*.
i also tried to boot under *recovery mode*, but loading stops at a certain point, and the output looks like this:

[INDENT]
[42.....911..] snd-hda-intel: can't be loaded
missing kernel or user mode driver snd-hda-intel
shpchp: already loaded
uhci-hdc: already loaded
( linia asta se repeta de 4 ori)
ehci-hcd: already loaded
<3>hw_random: RNG not detected
hw_random: can't be loaded
missing kernel or user mode driver hw_random
[/INDENT]

i also tried to install kubuntu 5.10, and the same thing happened.
i also tried to boot using the *live cd*, but it still stopped at *starting hotplug subsystem*

can anyone tell me what to do ?

thank you.

---

### Post by bluehand on 2005-12-12
Quick Solution:

1) Boot into recovery mode.
2) When the init scripts start running press ctrl c.
3) Use vi to edit /etc/hotplug/blacklist, and add a line for snd-hda-intel
4) Save the file and reboot

This should get you booting OK, but without any sound.

I also have a FS laptop with the same problem. I found out that Realtek (the audio chipset vendor) provide a Linux driver but I haven't installed it yet as it requires downloading the kernel sources and compiling.

Blue...

---

