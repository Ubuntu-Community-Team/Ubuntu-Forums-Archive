---
title: "Problems Partitioning USB Stick"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by LAF4SENS on 2008-08-06
Hi,

Per these instructions:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I also get an error at step 6 of Method 2:

```

6. Save and quit fdisk with 'w' to write the new settings.

    *

      I had an issue with this that every time I saved my partition setup using 'w', I'd get an:

      WARNING: Re-reading the partition table failed with error22: Invalid argument. The kernel still uses old table. The new table will be available at the next reboot.

      If this happens, and then checking with 'sudo fdisk -l' doesn't show the new partitions - here's a fix if you have a Windows OS, though I don't know why it works:

      Do nothing else with the drive. Insert into Windows (mine was XP) and format with Disk Management and use FAT32. Now, 'sudo fdisk -l' should see the two partitions under the drive. -neverard


```

I do a sudo fdisk -l and I can't seem to find the partition 2 (not there), even though I tried formating the USB stick in Windows.

Please Help,

Marc.

---

