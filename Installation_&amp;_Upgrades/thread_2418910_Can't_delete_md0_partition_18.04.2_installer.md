---
title: "Can't delete md0 partition 18.04.2 installer"
date: 2019-05-13
forum: Installation &amp; Upgrades
---

### Post by clarknova on 2019-05-13
I booted the 18.04.2 server installer (not live) in UEFI mode and got to the partitioning step. I created a new empty partition table and then a single partition on two disks (sdb and sdc), using all of the available space. I then created a RAID 1 device (md0) using all of the available space from these two partitions (sdb1 and sdc1) and designated the new partition as EXT4 mounted at /.

At this point I realised that I had forgot to create an EFI partition on the md0 device. The problem is that there doesn't appear to be a way to delete or resize the EXT4 partition that I already created on the device. If I highlight the RAID device and hit Enter, the screen simply refreshes after a few seconds. If I highlight the EXT4 partition and hit Enter, I get options to change the filesystem, label, mount options, mount point, etc, but there is no option to delete or resize the partition.

Is this a bug in the installer or am I doing something wrong?

---

### Post by clarknova on 2019-05-13
As an attempted workaround, I deleted the md0 device, deleted the partitions on sdb and sdc, then created a new RAID 1 device (md0) from the unpartitioned sdb and sdc devices. The partitioning tool then showed the md0 device with a single unconfigured partition occupying the whole md0 device. So the workaround was not effective, and landed me back in the same predicament with no way to make an EFI partition and root partition on the md0 device.

My next attempt was to use the Guided partitioning (whole disk) option instead of manual. This created the result that I wanted, with a ~500 MB EFI partition and an EXT4 root partition using the remainder of the space on the RAID device.

---

