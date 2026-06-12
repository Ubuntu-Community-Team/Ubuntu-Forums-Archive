---
title: "No Symbios/LSI 53c8xx support in 10.10 kernel"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-10-13
I have a PCI SCSI controller with this chipset that was working fine in 10.04 to drive a Polaroid Sprintscan 35 Plus scanner. Having just run the upgrade to 10.10, the scanner is no longer being seen. If I go into the controller BIOS the scanner is seen there, and running lspci shows the controller as
```
SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 04)
```
Running 
```
sudo modprobe -l | grep "sym"
```
shows only
```
kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
kernel/drivers/scsi/sym53c416.ko
kernel/drivers/usb/serial/symbolserial.ko
```
Seems like support for the 53c8xx chipset has disappeared?

---

### Post by srs5694 on 2010-10-13
I don't have 10.10 installed on anything, so I can't check this myself

```

find /lib/modules -name "*sym53c8xx*

```

This will show all the modules that match that name that exist, whether or not they're loaded. If the relevant module is present, you should be able to load it with "sudo modprobe sym53c8xx" (or whatever the complete name is), or perhaps an insmod on the complete path to the file. If necessary, you should be able to add that command to /etc/rc.local to get it to execute automatically when you boot.

---

### Post by Nick Payne on 2010-10-14
Running that find command just shows the same two sym53c* modules as I previously found with modprobe, so it looks as though the sym53c8xx module is not there in 10.10.

---

### Post by srs5694 on 2010-10-14
Then you'll have to recompile your kernel or track down a binary module built for the same kernel version used by Ubuntu 10.10. Maybe a Web search will turn up a suitable binary module....

---

### Post by Nick Payne on 2010-10-15
> Then you'll have to recompile your kernel or track down a binary module built for the same kernel version used by Ubuntu 10.10
As I had /home on a separate partition, it was easier to reinstall 10.04, which is what I did. Scanner now working again.

---

