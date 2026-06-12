---
title: "Ubuntu does not create /dev/sg devices ?!"
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by troutrou on 2004-11-05
Originally had problems with Sane not detecting my SCSI scanner, despite it being normally very well supported (AGFA Snapscan 1236s)

Turned out that Ubuntu did NOT create the SCSI "/dev/sg0" device during install.

If I run "modprobe sg" it creates the device, and Sane can then see my scanner fine, but the problem is that everyime I restart my machine, the device has gone, and I must therefore run "modprobe sg" again... not very practical.. :o(

How come Ubuntu did not create the SCSI device right from the start, and how come it disappears when the machine is rebooted, is there a way to make it permanent ?

Looks like  huge bug to me, no ?

I mean, when I installed Ubuntu, I turned my scanner on, and it detected it fine (attested by the device manager), so why didn't it create the /dev/sg0 device to go with it at the same time ??

Any help will be gratefully appreciated...

Vince

---

### Post by Kadin2048 on 2006-03-24
I am bumping this (I know, ancient) thread because I think it's the same problem I'm having now with a tape drive...

A program I'm using ("mtx") wants the generic scsi devices, like /dev/sg0, but Ubuntu doesn't create them. I need to find a way to make sure they're there, which survives rebooting. I don't want to have to modprobe every time I reboot.

Anyone have any ideas?

---

### Post by DavidRa on 2006-05-22
If you are running

modprobe sg

and getting your devices, try adding a new line containing just "sg" to the end of /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
**sg**

---

