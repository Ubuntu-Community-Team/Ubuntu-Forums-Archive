---
title: "Lenovo P50 with NVME - Ubuntu 18.04 - does not have /dev/sd_ entry for NVME drive"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by wb0gaz on 2018-09-30
I wish to install Ubuntu 18.04 on Lenovo P50 laptop with a Samsung 970 PRO NVME storage device, with intent that the machine boot Ubuntu 18.04 from that device. Problem is that the Ubuntu 18.04 installer does not see the NVME device in the /dev/sd_ table.

There is no other operating system in the machine (however, a previous storage device had Windows 7 installed and operable, however, that device has been replaced by the NVME storage device.)

The Samsung 970 PRO NVME storage device is new so I believe there is no existing partition table.

The laptop BIOS shows the Samsung 970 PRO NVME storage device as one of the boot options, so I believe it is physically available to Ubuntu installer.

I booted the USB drive containing Ubuntu 18.04 live installer to the guest session, started a terminal window, and found that there is no device for the NVME storage device in /dev (for example, I cannot use fdisk or gdisk to access the device to see or manage partitions.)

---

### Post by wb0gaz on 2018-09-30
False alarm - I didn't realize nvme devices are /dev/nvme___ rather than /dev/sda_. Once I realized this, everything else worked as expected.

---

