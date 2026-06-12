---
title: "Flashing cursor boot from USB"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by jcoom41 on 2011-12-29
Hello,

Ive Installed Ubuntu to several USB devices, such as a external USB Hardrive, and several USB flash drives, but when i go to boot to them pressing F9 for boot options and select the drive to boot from, all i get is a flashing cursor.

Also its not a live USB its the full installed Ubuntu on the USB.

Any ideas, would be really appreciated.

My Laptop
HP dv6-6134tx

---

### Post by Onthax on 2012-02-28
> **jcoom41 said:**
> Hello,

Ive Installed Ubuntu to several USB devices, such as a external USB Hardrive, and several USB flash drives, but when i go to boot to them pressing F9 for boot options and select the drive to boot from, all i get is a flashing cursor.

Also its not a live USB its the full installed Ubuntu on the USB.

Any ideas, would be really appreciated.

My Laptop
HP dv6-6134tx

I had a similar issue, on install to the USB drive, at the end click advanced, and make sure grub is installed on the MBR of your USB drive, not the first HDD

---

