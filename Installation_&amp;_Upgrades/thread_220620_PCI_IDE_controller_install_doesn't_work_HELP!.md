---
title: "PCI IDE controller install doesn't work HELP!"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by iric on 2006-07-21
Please help me out on this.

I have 4 different PCI IDE controllers and none works with Ubuntu 6.06 :(

As this is a real server I don't have any IDE on board, just SCSI but it is far too expensive to buy SCSI disks so went for a cheaper solution.

First had an old SIL 0680 (without the A) and it didn't work at all (does work on Fedora 2 though)

Now I ordered 3 others to be sure it works, but it still doesn't.

Other 3 cards:

IT 8212F no raid
IT 8212F RAID
SIL 0680A (latest 2006 bios)

They all won't boot from CD so I intstall from floppy (internet install) and that works ... until I reboot

On the SIL 0680A it gives ERROR 16 on GRUB (used reiserFS, should I just use EXT3?)

The IT won't install as it cannot find disk drive and gives a list with possibilities, but I don't know which to choose.

When installed on the SIL and after that booted from the IT gives:

ALERT! /dev/hda1 does not exist. Dropping to a shell!

So what can I do in order to get ubuntu 6.06 working on this system? Please help me out!

---

### Post by iric on 2006-07-22
anybody???

---

### Post by iric on 2006-07-22
tried about anything and still nothing... even with LILO, then I get a L 99 99 99 99 error..

---

