---
title: "lvm and partition problems"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by snafu7 on 2006-06-10
When booting from the 6.06 desktop cd and select start/install all is well until the start reaches "starting enterprise logical volume management" at which point I get errors similar to this:

[4294113.648000] Buffer I/O error on device dm-9, logical block 6302133
[4294xxx.508000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASK/ASCQ0x31/04
[4294xxx.508000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASK/ASCQ0x31/04
[4294xxx.508000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASK/ASCQ0x31/04
[4294xxx.508000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASK/ASCQ0x31/04
[4294131.648000] Buffer I/O error on device dm-9, logical block 6302134
etc

These repeat for about 15 minutes then the rest of the boot continues normally.

When installing for step 5/6 I selected 'manual partition' (Dual boot machine and I want to replace fedora4).  It then goes into a "Prepare partitions" and says "scanning all devices" and seems to scan for ever

Any one got any ideas ?
Hardware: 2 older IDE drives, SATA drive, AMD64, NF4 motherboard

Thanks in advance ...

P.S Checked CD for errors (none) and installed on 2nd PC without a hitch

---

### Post by DaBigUA on 2006-06-19
Sorry no one answered this query.  I have just encountered precisely the same problem, except I have dm-3 buffer i/o errors and different logical blocks.  Instead of waiting I interrupted the Enterprise LVM error message readout.  Like you, though, the partioner hung (mine at 50%,fwiw).  Similarly I have multiple IDE drives, a SATA drive, differently an Intel motherboard.  I also have two USB drives and a USB/flash memory reader.

---

### Post by DaBigUA on 2006-06-20
Following up my own post - I burned an install disk using the alternate 6.06 and installation ran without a hitch.

---

