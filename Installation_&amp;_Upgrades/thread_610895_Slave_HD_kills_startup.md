---
title: "Slave HD kills startup"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by rustyslacker on 2007-11-12
I'm on XUbuntu 7.10, which is installed on my 20GB master HD. Until about 10 minutes ago, I had a 30GB HD installed as a slave drive. I suspect it was causing random lockups-- I'd had to shut down forcefully a couple times, and since I've removed it there have been no lockups.

But the main problem is, when the slave was installed, XUbuntu would not start. Normally it would, but quite recently it decided to **** over the startup process. The bootloader would start, and then a ton of text would scroll on the screen, and end with:

```
[19.786297] Fixing recursive fault but reboot is needed!
```

After attempting to reboot, the message would change to:

```
[20.[some numbers]] Kernel panic - not syncing: Attempted to kill init!
```

Upon every boot, one of these two messages would display, and sometimes the numbers would change, but the first two digits were always 19 or 20. 

What do I do to keep the slave drive installed and working happily with XUbuntu?

EDIT: Specs..
Pentium 2 448 mhz
460-ish MB RAM (PC100/PC133)
Master HD: Western Digital 20 GB 
Slave HD: Western Digital 30 GB 
ATI Radeon 7000, 32 MB
HP CD-Writer 9100
WUSB54GC, running fine through ndiswrapper
Esoniq PCI audio thing

EDIT2: Apparently it's not caused by the slave HD. It just happened again (random lockup, followed by crash on reboot). At the time of the lockup I was running Firefox, Pidgin, and the Add/Remove programs manager. Ctrl+Alt+Backspace did not work, and the mouse cursor was frozen onscreen. When I tried to reboot, I got:

```
[23.415125]Kernel panic - Not syncing: fatal exception in interrupt
```
Rebooting again, I got:
```
[20.something]Fixing recursive fault but reboot is needed!
```
:<

Then I switched off the power strip, jiggled the power connector to the hard drive, switched the power strip back on, and booted normally. What's going on, and how do I make it work (with the slave HD installed)?

---

### Post by rustyslacker on 2007-11-12
I decided "screw it" and started a fresh install of Ubuntu 7.10 (Ubuntu this time, not Xubuntu). I started the install process, and left the house while the partitioning/formatting/file copying was going on. And I came back to find my computer frozen in the install. Ctrl+Alt+Backspace = nothing. Mouse movement = none. 

I reboot. Grub fails with "Error 15". I put in the Ubuntu CD and reboot. Kernel panic, not syncing.

This is ******* ridiculous-- even Windows puts me through less ****. I gotta say Ubuntu has just lost a user.

---

