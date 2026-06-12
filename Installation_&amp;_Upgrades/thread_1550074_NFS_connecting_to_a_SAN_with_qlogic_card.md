---
title: "NFS connecting to a SAN with qlogic card"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by dtd646 on 2010-08-10
I am trying to connect my Ubuntu server to an IBM SAN device via a qlogic fibrechannel card. I have gone onto the SAN and added my Ubuntu Host's HBA and everything looks good on that side. On the Ubuntu server, it looks like the device is registering properly:
 
Host: scsi4 Channel: 00 Id: 00 Lun: 01
Vendor: IBM Model: 1726-4xx FAStT Rev: 0617
Type: Direct-Access ANSI SCSI revision: 05
 
This may sound noobish, but how do I use NFS to present this LUN as a NFS share on my Ubuntu server? Any advice would be greatly appreciated!

---

