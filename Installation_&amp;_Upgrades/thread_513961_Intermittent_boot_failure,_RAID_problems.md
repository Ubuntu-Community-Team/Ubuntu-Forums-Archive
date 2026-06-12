---
title: "Intermittent boot failure, RAID problems"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by onlyconnect on 2007-07-31
I've installed Ubuntu server 7.04 on a new PC with 4 SATA drives. I am using software RAID.

I've configured each drive identically, with a small partition for boot and a large partition for everything else. I've set up /boot as RAID1 on the small partition. The other partitions are configured as RAID 5 with no spares. 

It's going OK, insofar as when I get a successful boot, the system runs very well. mdadm reports all is well with my RAID setup. However, I have two problems. Every time I shutdown, I get a fail on stopping md1 (the RAID 5 array). Most seriously, I get intermittent boot failure. It often goes alternately. I get a successful boot, then next time it hangs after:

md0 stopped
md1 stopped

If I wait a bit, something times out and I get a boot failure. It drops back to an emergency shell because there is not root volume available.

I then soft reboot and it often (but not always) succeeds. There seem to be three variations:

1. Success.
2. Sometimes I get a hang on hid-core.c USB HID core driver (I have a USB mouse connected).
3. The hang after md1 stopped as above.
  
Can't post boot logs because boot logging doesn't work at the moment either, unfortunately.

Tim

---

### Post by onlyconnect on 2007-07-31
Seems to be fixed, or at least much improved, by enabling AHCI in the BIOS, for the Sata drives.

Still get the md1 fail on shutdown, but no boot failures since.

Tim

---

