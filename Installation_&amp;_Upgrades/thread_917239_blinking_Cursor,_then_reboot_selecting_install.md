---
title: "blinking Cursor, then reboot selecting install"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by atomikn on 2008-09-11
I am trying to install Heron on the following hardware:

Gigabyte EP-43-DS3L mainboard (Intel P43)
2 1GB Kingston KVR800 memory modules
80 Gb Seagate SATA hard drive
OPTIarc SATA dvd burner
Asus EAH3450 (Ati) video card (PCIe)
no floppy

CD install:
After selecting 'install ubuntu' I get a flashing cursor for about 10 seconds and the pc reboots. Same result from 'check cd for errors'.

USB drive install
After selecting 'install ubuntu' I get to 'initrd.gz... ready' 
then the machine reboots. The 'default' option gets to ubninit/ (I think) then reboots.

Tried enabling AHCI, disabling AHCI. 
Tried noacpi noapic vga=XXX noirq nolapic

Tested memory, fdisked and formatted hdd. Tried latest ubuntu release, alternate install, version 7.

Installed XP home and it installed fine - was trying to shake out some sort of hardware issue.

Swapped out SATA optical drive for and IDE.

Any help is appreciated.

---

### Post by murrie on 2008-09-12
[SIZE="3"]GIGABYTE
EP43-DS3R S-series[/SIZE]
The problem you are having, is in the bios. You must go into the bios of this motherboard and enable ahci as this is what ubuntu requires. Go into the integrated peripherals, then change SATA-RAID to AHCI MODE and then all is well. Had an asus board and this wasn't required, but on this gigabyte board seems to be the case and works fine, just slows down the post boot time
a bit, but otherwise fine.

---

