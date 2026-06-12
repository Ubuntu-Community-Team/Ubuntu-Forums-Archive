---
title: "HD Controller Order Problem"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by likemike64 on 2006-10-02
I have a computer with a built-in Adoptec SCSI controller and a add-in SATA HD controller card. I am moving this computer from Fedora Core to Ubuntu server. Fedora taged the SCSI controller as SDA and the SATA controller as SDB, Ubuntu reverses the order (SCSI as SDB and SATA as SDA) on install.  I want to use the SCSI HD for / and the SATA for /home (as I did in Fedora). Is there a way to change the way Ubuntu ID's the controlers so that / and /boot are on the SCSI (like Fedora did) instead of the SATA?

Thanks in advance for any help.

---

