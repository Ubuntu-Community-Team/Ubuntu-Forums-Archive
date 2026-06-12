---
title: "SIL 3124 Problem"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2011-05-15
I have Kubuntu Natty 11.04 with 2.6.38.6 custom kernel. The system works fine other than ....

I have a SIL 3124 PCI eSATA card to which is attached a SIL 3132
external disk box with two disks. The external disk box was configured with SIL's Windows utility to have the disks accessed individually, not "hardware" RAID. 

On an earlier version of linux I was able to see the two disks individually and to use them in a mirrored linux software RAID volume. After several upgrades leading to the current configuration above, I'm no longer  to see the two disks. Specifically, fdisk -l does not show the two external disks.

I have modules ide_core, piix, sata_sil and sata_sil24 loaded. For boot, /var/log/messages shows:


sata_sil24 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
scsi6 : sata_sil24
scsi7 : sata_sil24
ata7: SATA max UDMA/100 host m128@0xfbdffc00 port 0xfbdf8000 irq 17
ata8: SATA max UDMA/100 host m128@0xfbdffc00 port 0xfbdfa000 irq 17

Which I think(?) refers to the two external disks, but fdisk -l does not show them, nor does parted, and I'm unable to access them.

Anyone know what's wrong and how to fix??

Thx, Gus

---

### Post by gus_zernial on 2011-05-15
Problem solved - it was a bad cable.  Gus

---

