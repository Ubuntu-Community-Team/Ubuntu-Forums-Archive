---
title: "Cannot boot kernels later than linux-image-4.8.0-22-lowlatency"
date: 2017-04-19
forum: Installation &amp; Upgrades
---

### Post by fredringwald on 2017-04-19
I installed Ubuntu Studio several years ago and have been running it successfully through multiple upgrades on my MSI FM2-A55M-E33 motherboard running an AMD A8-5600K APU with Radeon graphics. I recently upgraded to Ubuntu 16.10, then to Ubuntu 17.04. However, I have not been able to boot any kernel later than linux-image-4.8.0-22-lowlatency. I have tried numerous lowlatency and generic kernels with similar unsuccessful results. My latest attempt was with linux-image-4.10-0-19-generic. In each unsuccessful boot attempt, the boot appears to proceed normally until just before the point where the system announces the Ubuntu version and mounts the hard drive partitions. It then blanks the screen, returns to the BIOS boot screen, then the GRUB menu. I believe that it is because the hard drive partitions fail to mount that I have no information logged regarding the boot failures in the dmesg ring buffer, or in /var/log/syslog or /var/log/kern.log.

---

