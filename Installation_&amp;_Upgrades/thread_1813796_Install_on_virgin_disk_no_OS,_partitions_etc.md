---
title: "Install on virgin disk: no O/S, partitions etc"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by 1gnoramus on 2011-07-28
I have replaced the internal 160GB SATA disk on a laptop after it bounced down a flight of stairs.
Have tried loading 11.04 from memory stick but it can't see the disk. 
10.04 disk manager can see the disk (after a restart). It is not showing the disk serial numer nor firmware version. Location is Port 1 of SATA Host Adapter; Device: /dev/sda; Capacity 0 bytes.
Attempting to format the ATA Toshiba MK1676GS with Master Boot Record scheme produces error:
"Error creating partition table: helper exited with exit code 1: In part_create_partition_table:device_file=/dev/sda, scheme=0
ped_device_get() failed"

Have a missed a vital step? Duff disk? I've read that it should format ok from the install USB. 
Any thoughts gratefully received.
Thank you

---

### Post by jerrrys on 2011-07-28
sounds like more than the hdd got mess up in the bounce down the stairs.  some computers have diagnostics built into BIOS

---

