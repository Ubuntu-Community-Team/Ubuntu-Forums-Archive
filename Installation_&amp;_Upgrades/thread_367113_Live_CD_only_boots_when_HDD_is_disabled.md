---
title: "Live CD only boots when HDD is disabled"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Rofo on 2007-02-21
Hi,

I just assembled an ASUS m-ATX board with SATA HDD and SATA CD. Works fine with XP. However, when trying to boot Ubuntu LIVE-CD loading stops halfway with the message:

"cp: unable to open /root/var/log: no such file or directory"

and I get a text prompt.

If I disconnect the harddrive booting works fine though! But the whole idea is to install Ubuntu on the drive which is then not possible.

-- Robert

---

### Post by maxamillion on 2007-02-21
try it with "no acpi" option at boot

---

### Post by Rofo on 2007-02-21
Well, tried it but it did not help.

-- Robert

---

### Post by Kateikyoushi on 2007-02-21
Try to boot using these "dma=off acpi=off".

---

### Post by Rofo on 2007-02-21
I solved the problem! I moved the HDD Sata cable to another connector on the motherboard so that the drive became Master on a different channel than the (slave) CD-ROM.

-- Robert

---

