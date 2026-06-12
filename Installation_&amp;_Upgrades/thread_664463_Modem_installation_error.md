---
title: "Modem installation error"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by ranjithnair on 2008-01-11
When I try to install my modem driver I get this error


sudo dpkg -i hsflinmodem_4.06.06.02-2_i386.deb
(Reading database ... 95352 files and directories currently installed.)
Preparing to replace hsflinmodem 4.06.06.02-2 (using hsflinmodem_4.06.06.02-2_i386.deb) ...
Removing old /usr/lib/hsf
Unpacking replacement hsflinmodem ...
Setting up hsflinmodem (4.06.06.02-2) ...
Linux HSF softmodem drivers, version 4.06.06.02
grep: /proc/ksyms: No such file or directory
[: 103: 100: unexpected operator
HSF drivers currently don't support SMP (Symmetric Multi-Processing) kernels.
First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.
The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).
Verify that the proper options for your system are selected,
and that CONFIG_SMP ("Symmetric multi-processing support" under
"Processor type and features") is disabled, as this driver is
presently designed to work on single-processor machines.
Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "hsfconfig".
dpkg: error processing hsflinmodem (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hsflinmodem

Please help!!!!

---

