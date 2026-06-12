---
title: "Printer port problem"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by jamerrett on 2008-10-27
Hope that someone out there can help me!I am a complete newbie to Linux  I have installed Hardy heron cannot get it to recognize my Parallel port.I have also downloaded all the available updates. I understand that in Linux it is known  as /dev/lp0. I have trawled the net for hours trying to figure it out, and yes I do know RTFM! but I cannot find any thing. I think that maybe the Parallel port is either not installed at all or is incorrectly installed.

---

### Post by lemming465 on 2008-10-28
If the System -> Administration -> Printing application for printer configuration doesn't work out for you when you pick "Server -> New" and select "Lpt 1", then it's possible that your parallel port doesn't have a driver module loaded in the kernel.  That could either be because you have unsupported hardware, or because of some quirk of the install process.  We'll need more information to figure things out.  This will require opening up an Applications -> Accessories -> terminal window and doing some command line stuff.

* Was the printer turned on when you did the install?

* Does "ls -l /dev/lp0" yield output like:
crw-rw---- 1 root lp 6, 0 2008-10-27 20:34 /dev/lp0

* Does "lsmod | grep par" yield something like:
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc

* What happens if you do "sudo modprobe -v parport"?

* What kind of computer is it?  The vendor, model, CPU, motherboard, and southbridge chipset are the most interesting things to know.  Either vendor + model or motherboard is enough to give us a clue.  We can probably deduce the chipset from that, and figure out if there is a support issue with the hardy heron kernel and the parallel port.

---

