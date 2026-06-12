---
title: "Can I just install Ubuntu to a USB drive?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Vinze on 2007-04-25
Hey, I followed [a tutorial from PendriveLinux.com](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/) to install Ubuntu Edgy Eft onto a USB disk, but I'm not altogether happy with it because 1) it behaves like a LiveCD and adding accounts and disabling times login won't work and 2) because it still is Edgy Eft. Now I was wondering, can I just insert a (X)Ubuntu cd and choose to install it to /dev/sda ?

Thanks in advance.

---

### Post by NeoTaoistTechnoPagan on 2007-04-26
A USB thumb drive will be a bit slow compared to a USB hard drive. I've never compared the read/write times against a CD, but you could probably do that with hdparm.

```
hdparm -tT /dev/hdX
```
Where 'X' is the drive you want to test. Assume 'sdX' for USB drives, SCSI, or SATA.

---

### Post by Vinze on 2007-04-26
> **NeoTaoistTechnoPagan said:**
> A USB thumb drive will be a bit slow compared to a USB hard drive. I've never compared the read/write times against a CD, but you could probably do that with hdparm.

```
hdparm -tT /dev/hdX
```
Where 'X' is the drive you want to test. Assume 'sdX' for USB drives, SCSI, or SATA.

I'm sorry, I'm not too much at home in the world of hardware so I don't understand much of your reply... :(

All I wanted to know was whether I could, during the installation process, just select /dev/sda (my USB drive) as the installation location, instead of /dev/hdb which I would otherwise use.

---

