---
title: "ALERT! /dev/disk/by-uuid/bec6d6a1-2261-4972-bb39-6d88cee4f048 does not exist."
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by danprice1 on 2010-10-16
Hey, I'm new here, and to Ubuntu really.
Basically, today I installed Ubuntu on my Toshiba NB200 to dual boot with XP. The installation went okay (I think) but after, when I rebooted, and selected Ubuntu from the possible selections, I got this message:

Quote:
Gave up waiting for root device.
Common problems:
-Boot args (cat /proc/cmdline)
-check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/bec6d6a1-2261-4972-bb39-6d88cee4f048 does not exist.
Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1Ubuntu5) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)
Sorry if this is a stupid question, but does anybody know how to solve this?

Thank you so much

---

### Post by oldfred on 2010-10-16
I found this in my notes:

ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"

---

### Post by richlowe101 on 2010-11-11
This fixed it for me too, my BIOS was setting SATA behaviour to default to raid. Suspect that this kernel dislikes raid in some way.
Can you mark this thread as solved?

---

### Post by Quackers on 2010-11-11
It's not your thread :-)
Only the OP can mark the thread closed.

---

