---
title: "qlogic fibre channel driver - not there."
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by dmallery on 2004-11-29
hi

i have done a few ubuntu installs prior to this with success.  however on a machine with a scsi cdrom and a qlogic fibre channel controller, it fails to install the driver module. 

just checking to see if that is the case, or i missed something.  i'd like to make a machine with fibre channel only.

thanks!

dave mallery

---

### Post by brianfinley on 2005-04-25
[QUOTE=dmallery]hi

i have done a few ubuntu installs prior to this with success.  however on a machine with a scsi cdrom and a qlogic fibre channel controller, it fails to install the driver module. 

just checking to see if that is the case, or i missed something.  i'd like to make a machine with fibre channel only.

thanks!

dave mallery[/QUOTE]
 For some reason, which I'd like to know, Ubuntu has omitted many of the qlogic drivers from their binary kernel.  The source appears to exist, but the standard kernel config methods don't indicate that they are available for inclusion when using the Ubuntu source.  (2.6.10 and 2.6.11 series ubuntu kernel).

Ubuntu, what gives?  I need the qla2300 driver and have had to compile and install my own kernel.  I'd really like to be able to use and promote ubuntu as is.

Cheers, -Brian

---

### Post by brianfinley on 2005-04-29
Please see this thread:

[http://www.ubuntuforums.org/showthread.php?t=24022&highlight=qlogic](http://www.ubuntuforums.org/showthread.php?t=24022&highlight=qlogic)

---

