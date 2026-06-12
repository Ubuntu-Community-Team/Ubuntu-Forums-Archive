---
title: "USB detected beofre the sata disks are"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by Dennis Beekman on 2010-10-19
I  used to run ARC linux and Windows 7 on my computer and i am now trying to install Ubuntu 10.10 X86_64

When i used the live disc of Ubuntu 10.04 and load the installer it finds my four harddrive they way it should... sda,sdb,sdc,and sdd...
When i however try the same with ubuntu 10.10 it displays my usb cardreaders drives first and then my hardrives as sde sdf sdg and sdh.

I tried installing ubuntu with the reader unplugged and then reconnecting it after installation...
But when i then boot with the reader attached it says it cannot mount drives sda,sdb,sdc and sdd becuase they are not ready.
I think it is again detecting the usb cardreader before the sata controller ...

Is there a way for me to alter the boot detection order so it will find my harddrives first and then the usb cardreaders ports ?

* i tried google but it didn't get me anywhere, and ubuntu seems not to have a rc.conf file in /etc/ like Arch does. *

---

### Post by ronparent on 2010-10-19
What happens if you boot the live cd with the usb's unplugged, and then plug them in while running and before installing? And then installing with the reader plugged in.

---

