---
title: "Bad page state in process 'modprobe'"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Ditiris on 2007-07-05
I *thought* I successfully installed Ubuntu 7.10 x64, but I have yet to be able to boot the installation.  

I have a Gigabyte GA-965P motherboard, Q6600, 4 GB RAM, 8800 GTX.  Note that the chipset is incorrectly identified as a 965G in the error messages below, instead of a 965P; I have no idea if that matters or not.

I am booting to the following option on the GRUB boot menu:
Ubuntu, kernel 2.6.20-15-generic (recovery mode)

Here's the last bit of console messages before the system hangs:

```

*Starting basic networking... [OK]
*Starting kernel event manager... [OK]
*Loading hardware drivers...
[    43.288051] input: PC Speaker as /class/input/input3
[    43.320373] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    43.321851] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    43.323796] agpgart: Detected an Intel 965G Chipset.
[    43.338657] Bad page state in process 'modprobe'
[    43.338659] page:ffff81011fd3e308 flags:0x0000000000000000 mapping:0000000000000000 mapcount:1 count:0
[    43.338660] Trying to fix it up, but a reboot is needed
[    43.338661] Backtrace:
[    43.338712] Bad page state in process 'modprobe'
[    43.338714] page:ffff81011fdb9860 flags:0x0000000000000000 mapping:0000000000000000 mapcount:1 count:0
[    43.338715] Trying to fix it up, but a reboot is needed
[    43.338716] Backtrace:
[    43.338717]
[    43.338718] Call Trace:
[    43.339539]
[    43.339540] Call Trace:

```

The numbers on the left change for reboots, but the rest of the console output remains the same.

Please help!

---

### Post by marwooj on 2007-07-17
the same for me, any recipes?

---

### Post by kugel. on 2008-01-25
Sorry for reviving this old thread, but I have the same problem and I do need help.

---

