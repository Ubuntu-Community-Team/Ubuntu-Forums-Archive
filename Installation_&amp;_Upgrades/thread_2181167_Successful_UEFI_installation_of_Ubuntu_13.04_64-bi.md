---
title: "Successful UEFI installation of Ubuntu 13.04 64-bit on Gateway DX4380G"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2013-10-16
Computer: Gateway DX4380-G-UW308
Processor: AMD A6-6400K
Total Memory: 6GB
BIOS Version: 2.15.1226
BIOS Vendor: Acer
System BIOS version:  P11-A1

Secure boot is disabled and "Launch CSM" set to "Always".

I booted from a 64-bit Ubuntu 13.04 live CD and verified everything worked.  Then, I installed Ubuntu, letting it wipe out the hard drive and completely replace the Windows 8 installation.  After the installation completed, the system wouldn't boot from the hard drive, so I ran the "Boot-repair" utility, which I installed in another live CD session.  After running the "Boot-repair" utility, the system is able to boot successfully from the hard drive.

I wanted to post this information in the event it might help someone else. :)

Peace...

---

