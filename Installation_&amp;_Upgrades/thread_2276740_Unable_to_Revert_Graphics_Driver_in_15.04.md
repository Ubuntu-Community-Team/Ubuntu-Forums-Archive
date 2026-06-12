---
title: "Unable to Revert Graphics Driver in 15.04"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by Prescience500 on 2015-05-04
After having finished configuring everything the way i like it and transferring all data over, I noticed that I had installed the legacy NVIDIA proprietary driver and that the newer one was recommended. I upgraded to the newer 340 driver that was recommended and from then on, the computer would freeze every time I rebooted.

To fix it, I booted to the safe mode command prompt. From there, every attempt to uninstall the driver failed as did every attempt to downgrade to the previous version or even to the mesa driver. Instead, it kept giving me the following output:

W: Not using locking for read only lock file /var/lib/dpkg/lock
E:  Unable to write to /var/cache/apt/
E:  The package lists or status file could not be parsed or opened.

I eventually found a way to uninstall the driver. Then, I had the bright idea to the install the nvidia driver that I knew worked (nvidia-304-updates)...while still in safe mode. Now, every time I try to boot, whether in regular mode or safe mode, it results in a kernel panic.

How can I fix this?

---

