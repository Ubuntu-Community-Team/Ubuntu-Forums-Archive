---
title: "Zero Channel RAID"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by cbhargava on 2007-02-14
Last night I had to install Linux on a dual Xeon machine with Adaptec ASR-2010s zero channel adapter. I tried, Ubuntu 6.06 & 6.10, CentOS 4.4, Fedora Core4. No success.

Hardware:
Motherboard: SuperMicro X5DP8-G2
ZCR: Adaptec ASR-2010s
Memory: 4GB
CPU: Dual Xeon 2.4Ghz
Drives: 3x Seagate 73GB SCA drives on single backplane
ID0: OS drive
ID1: First drive for RAID-0
ID2: Second drive for RAID-0

I installed Ubuntu 6.06 and it gave me folloring errors
[42949388.360000] iop0: device already claimed
[42949388.360000] iop0: DMA / IO allocation for I2O controller failed

Despite of errors, os installed ok on /dev/i2o/hda. The RAID drive was untouched and had device name /dev/i2o/hdb. I was able to partition it and mke2fs on the raid drive.

After the OS isntall was complete, the machine rebooted and failed the boot process with following errors:

[15.190943] iop0: device already claimed
[15.190996] iop0: DMA / IO allocation for I2O controller failed.
ALERT! /dev/i2o/hda1 does not exist. Dropping to a shell!

CentOS and FC4 did not even detect the drives even after installing the driver. FreeBSD 6.2 installed okay without any problems.

After this, I added a IDE drive as primary master and installed Ubuntu 6.10 on it and after the boot the machine. It worked! :)  As the OS drive was on the backplane, I couldn't use a SCSI drive.

Conclusion: Ubuntu cannot be installed on a standalone drive controlled by the ZCR.

Are there any workarounds so that I don't have to use an IDE drive as OS drive? Both 6.06 and 6.10 seen to behave exactly same on the hardware. Any fixes coming? :confused: 

Regards,

cbhargava

---

