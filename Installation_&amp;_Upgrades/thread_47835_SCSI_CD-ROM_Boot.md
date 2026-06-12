---
title: "SCSI CD-ROM Boot"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by cronos_ on 2005-07-10
Hello,

I have a problem booting the Installation CD. The boot process hangs on stage 1.5.

I'trying to boot from a scsi cdrom drive attached to an "Advance Peripherials 2941 UW" scsi controller card.
The scsi BIOS is the most recent, but in my case that means it is from 2001. The linux driver normally used for this card is sym53c875 (i.e. symbios chipset)

Other ISOLINUX boot CDs boot without problems (but they use stage1/stage2 and not stage1.5).

What possibilities do I have?
Boot floppy? IIRC the ubuntu boot floppy only supports IDE drives.
USB boot? I could boot from an USB stick but where do I get the appropriate boot image (installation over the network, then).

I'd be greatful for any help.

cronos_

---

