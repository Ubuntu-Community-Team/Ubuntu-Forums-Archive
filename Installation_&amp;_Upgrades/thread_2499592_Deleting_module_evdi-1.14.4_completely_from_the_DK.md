---
title: "Deleting module evdi-1.14.4 completely from the DKMS tree."
date: 2024-08-01
forum: Installation &amp; Upgrades
---

### Post by mylesmorales1940 on 2024-08-01
Today after running the following command:   sudo apt update && sudo apt upgrade -y the held back kernel 6.8.0-40-* were updated and moments later my AOC usb monitor stopped working. I decided to reinstall display link latest driver for ubuntu 6.0.0-24 and received the following:

sudo ./displaylink-driver-6.0.0-24.run
Verifying archive integrity...  100%   MD5 checksums are OK. All good.
Uncompressing DisplayLink Linux Driver 6.0.0  100%  
Distribution discovered: Ubuntu 22.04.4 LTS


Installing
[ Installing EVDI ]
[[ Installing EVDI DKMS module ]]
Creating symlink /var/lib/dkms/evdi/1.14.4/source -> /usr/src/evdi-1.14.4


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...
make -j8 KERNELRELEASE=6.8.0-40-generic all INCLUDEDIR=/lib/modules/6.8.0-40-generic/build/include KVERSION=6.8.0-40-generic DKMS_BUILD=1...(bad exit status: 2)
sh: 0: getcwd() failed: No such file or directory
ERROR (dkms apport): binary package for evdi: 1.14.4 not found
Error! Bad return status for module build on kernel: 6.8.0-40-generic (x86_64)
Consult /var/lib/dkms/evdi/1.14.4/build/make.log for more information.
Deleting module evdi-1.14.4 completely from the DKMS tree.
ERROR: Failed to install evdi to the kernel tree.

This kernel update has been held back for awhile and not sure who decided to release it. But this the results of updating the kernel to 6.0.0-24 please advise.

Myles

---

### Post by mylesmorales1940 on 2024-08-02
I resolved the issue. I am thinking the new kernel includes the latest evdi. After researching I decided to remove the multiple evdi's, rebooted ubuntu 22.04.4 LTS laptop, plugged in the usb AOC monitor and the monitor is working. My issue is resolved.

---

