---
title: "Ubuntu 10.04 server i386 dual boot install"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by krisvdm on 2010-08-17
Im trying to install Ubuntu server for DVD/CD iso.
The mdsum is correct:
 md5sum ubuntu-10.04-server-i386.iso 

gives
  15342636441181f7a19c65984b44e24c  ubuntu-10.04-server-i386.iso


I have tried it a number of times and the same sequence re-occurs:
The first error occur during “Installing the base system”
First sign is a red screen displaying a “Debootstrap warning”  
After a few re-tries the system defaults back to the Installer menu:
I then select to post the debugger logs to a web server that starts:
the first sign of problems in syslog are:
-----------------------------------------------------------------------------
Aug 17 09:35:35 net/hw-detect.hotplug: Detected hotpluggable network interface lo
Aug 17 09:35:37 hw-detect: Loading PCMCIA bridge driver module: i82365
Aug 17 09:35:37 kernel: [  268.912151] Intel ISA PCIC probe: not found.
Aug 17 09:35:38 hw-detect: FATAL: Error inserting i82365 (/lib/modules/2.6.32-21-generic/kernel/drivers/pcmcia/i82365.ko): No such device
Aug 17 09:35:38 apt-install: Queueing package udev for later installation
-----------------------------------------------------------------------------
This is a normal PC without PCMCIA

Then there are further errors about “dpkg: error processing initramfs-tools”

Has anybody been able to install  ubuntu-10.04-server-i386 on a normal PC?

---

### Post by lechien73 on 2010-08-17
The "Deboostrap warning" often refers to corrupt installation media, so although the checksum is correct, errors could have crept in when burning the disc.

Try burning it again at 2x or even 1x speed - maybe with a different brand of discs.

A second option is to run a memory test - sometimes faulty memory can cause this problem.

---

### Post by krisvdm on 2010-08-18
I did a cd/dvd integrity check after bootup and it came out fine.
I re-wrote the dvd anyway and came up with the same error.
I re-wrote the CD four times now.
I did the DVD integrity check on two different CD's - both times fine.


I always get the same message:
--------------------------
Aug 18 08:59:14 hw-detect: Loading PCMCIA bridge driver module: i82365
Aug 18 08:59:14 kernel: [   18.063084] Intel ISA PCIC probe: not found.
Aug 18 08:59:14 hw-detect: FATAL: Error inserting i82365 (/lib/modules/2.6.32-21-generic/kernel/drivers/pcmcia/i82365.ko): No such device
Aug 18 08:59:14 apt-install: Queueing package udev for later installation
--------------------------

is it possible that the md5sum is correct, but the download is still wrong?

it complains about a PCMCIA device?  This is not a laptop.

---

### Post by krisvdm on 2010-08-18
the syslog file also contains complaints about packages that do not exist. eg:
---------------------------------------
Aug 18 08:59:25 main-menu[423]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Aug 18 08:59:25 main-menu[423]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
---------------------------------------

---

### Post by lechien73 on 2010-08-18
Could you attach the entire syslog as a text file, please? I think the PCMCIA warnings might be a bit of a red herring. I still wouldn't rule out faulty RAM - have you been able to run a memory test?

---

### Post by krisvdm on 2010-08-19
I Have tested the memory twice without getting errors, one about a  week ago and again today.
(I ran it for about 10 minutes and then exited).

I attach the first part of the log in five parts due to attachment and file-size constraints on this forum

---

