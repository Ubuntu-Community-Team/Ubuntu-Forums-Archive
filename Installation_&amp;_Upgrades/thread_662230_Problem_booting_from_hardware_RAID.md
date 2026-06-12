---
title: "Problem booting from hardware RAID"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by dave on 2008-01-08
Hi All!

I am having a problem getting my system to boot, and was wondering if anyone had ideas.  I am using a true-Hardware RAID 5 setup.  I have a RocketRaid 2300 card with 3x500GB disks in a Raid5 setup.  The driver I am using is  rr2300_00.ko  which I downloaded from the manufacturers website.

I was able to install ubuntu by compiling, and inserting the raid-module in the liveCD and everything was working.  Knowing that the kernel lacked support for the card, I chrooted to the new install and ran `apt-get install linux-source`.  So I'm at the point of playing with the kernel to have it boot.  I patched the ubuntu kernel to add support for my device.  I compiled it in, and it appears to be "somewhat" working.

When I try to boot my system my GRUB line is as follows:

```

root (hd0,2)
kernel /boot/vmlinuz-2.6.22.9 root=/dev/sda3 ro      (i have also tried adding noacpi  .. and  acpi=off )

```

THe outpt from the kernel is as follows (abriged)

```

rr2310_00:channel [0,0] started successfully
rr2310_00:channel [0,1] started successfully
rr2310_00:channel [0,2] started successfully
scsi0 : rr2310_00
scsi 0:0:0:0: Direct-Access   HPT   DISK_0_0    4.00 P : 0 ANSI: 0
...
VFS: Cannot open root device "sda3" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

I personally am out of ideas to try, is there something I need to do to tell the kernel to look at the raid-array for partitions?  if so how?

I thank you all in advance for any help!

--
Dave

---

