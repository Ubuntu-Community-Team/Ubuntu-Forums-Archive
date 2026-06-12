---
title: "64GB SSD and 2x3TB RAID0 ISSUE after installation"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by chewedtoothpick on 2012-08-16
I installed Ubuntu 12.04 Desktop on the 64GB SSD without problems.

I configured via onboard raid that two identical 3TB drives will operate as RAID0 at 128 stripe at max size.

Once Ubuntu is booted up, I goto Disk Utility and it shows all 3 drives on the SATA Host Adapter with [RAID mode] showing too. It reports that each drive is 3TB 3TB and 64GB as expected. However, under Peripheral Devices a 1.6TB hard drive appears.

At the time of installation when I had the option to chose which disk to install to, I also noticed it reported a 1.6TB drive and the 64GB SSD.

The plan was to install the OS on the SSD and use the RAID0 2x3TB drives for file storage.

When I un-raid the two 3TBs the 1.6TB disk goes away...

How can I get Ubuntu to recognize the RAID Array as 6TB like it should?

---

