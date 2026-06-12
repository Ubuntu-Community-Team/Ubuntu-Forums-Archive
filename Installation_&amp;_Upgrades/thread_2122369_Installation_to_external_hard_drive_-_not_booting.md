---
title: "Installation to external hard drive - not booting"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by Alan.Brown on 2013-03-04
I have an Iomega eGo 300GB USB external hard drive.   I have installed Lubuntu to a partition on the drive.  

When I tried to reboot from the external drive I get the message
> [B]file system not recognised 
 grub rescue>[/B]

I went into Xubuntu on the internal hard drive, mounted the external drive and entered
> **sudo update-grub**  - it showed that it had found the Lubuntu installation on the external drive
then I entered
> **sudo grub-install /dev/sdc**  (sdc is correct for the external drive)

When I tried to reboot from the external drive, the system ignored it and booted straight from Xubuntu on the internal drive - ***with no boot menu***.

I have successfully installed Lubuntu on a USB Flash drive before.

Can anyone help please

Tia

Alan

---

