---
title: "Where's USB moved to on Gutsy?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by chriscr on 2007-10-19
I'm trying to get my Topfield Hard disk Video Recorder to transfer files via USB to Gutsy with a program called puppy. This all worked fine under Feisty.

But now puppy reports:
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory

lsusb shows the Topfield is seen as connected:
Bus 004 Device 004: ID 11db:1000 Topfield Co., Ltd. PVR
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 049f:0051 Compaq Computer Corp. KU-0133 Easy Access Interner Keyboard
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Puppy has this option:
 -d <device>    - USB device (must be usbfs)
                  for example /proc/bus/usb/001/003

but this is what happens:
ERROR: Can not open /proc/bus/usb/004/004 for read/write: No such file or directory

Which would seem to be right since /proc/bus/usb is Empty.

Where have the USB devices gone? Now what do I do?

Thanks for any help,
chriscr.

---

### Post by bekowsquap on 2007-10-19
I'm having the same issue. I've posted on the How To thread here

[http://ubuntuforums.org/showthread.php?t=307216&page=2&highlight=topfield]("http://ubuntuforums.org/showthread.php?t=307216&page=2&highlight=topfield")

---

### Post by Mach1US on 2007-10-20
got the same problem when trying to write to /proc/bus/usb/devices
Where have they moved it ????:confused:

---

### Post by chriscr on 2007-10-27
> **bekowsquap said:**
> I'm having the same issue. I've posted on the How To thread here

[http://ubuntuforums.org/showthread.php?t=307216&page=2&highlight=topfield]("http://ubuntuforums.org/showthread.php?t=307216&page=2&highlight=topfield")

There is now a solution to this problem at the thread above.
Thanks for all the help.

chriscr.   :)

---

