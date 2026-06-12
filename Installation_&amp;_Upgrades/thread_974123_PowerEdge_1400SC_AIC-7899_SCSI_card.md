---
title: "PowerEdge 1400SC AIC-7899 SCSI card"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by ddaskey on 2008-11-07
After much fuss, I finally figured out that the PowerEdge 1400SC is 'hardwired' to boot from SCSI even if you have IDE drives in there and no SCSI devices connected.  It still tries to boot from a SCSI device, and when it doesn't find it, it fails to boot.  I disabled the SCSI in BIOS and guess what, it boots from the IDE disk.  So now that I understand what it is doing, looking at the SCSI BIOS, it does not appear to have an option to NOT have it boot, or TURN-OFF boot from SCSI.  Is there such a way to do that?  As I mentioned, the on-board SCSI is Adaptec AIC-7899.

---

