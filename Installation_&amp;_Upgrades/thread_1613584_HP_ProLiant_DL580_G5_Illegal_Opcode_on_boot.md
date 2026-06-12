---
title: "HP ProLiant DL580 G5: Illegal Opcode on boot"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by eblume on 2010-11-04
After a nightmarish 24 hours, I've successfully installed Ubuntu 10.04 x86-64 Server on an HP ProLiant DL580 G5 server with an added P800 Raid Controller device. I wanted to make a public record on the steps to finish the installation in case it helps anyone in the future.

The issue we were running in to was the message "Illegal Opcode" given after BIOS startup before the OS could load, even after a successful OS installation. HP support confirmed that this message is given when the MBR on the boot controller does not refer to a valid bootable partition.

First, our configuration (after several troubleshooting iterations - I'll leave out those steps):

HP ProLiant DL580 G5 with 32GB ECC-RAM, storage:
* 2x 70GB SAS storage via p400 Raid Controller, configured as 140GB RAID 0 device ("/dev/cciss/c1d0"), designated in the raid configuration manager (ORCA) as the Boot Controller
* 24x 1TB SAS storage via p800 Raid Controller, configured as 2x 10TB RAID 6 devices ("/dev/cciss/c0d0" and "/dev/cciss/c0d1")

In BIOS, the boot settings were:

Boot order was set to CD, USB, Floppy, Hard Drive, Ethernet
Hard Drive order was set to p400, IDE, p800  (note that there were no IDE drives, but for some reason the BIOS wasn't allowing us to move that device in the order.)

c1d0 was partitioned as:
* primary #1 - "/boot" - 2GB  - ext2
* extended #5 - "/" - 100GB - ext4
* extended #6 - swap - remainder (~38GB) - swap

c0d0 and c0d1 were partitioned partitioned with lvm. Note that small chunks (~1MB) were left 'free' on either side of the 10TB lvm partitions, I assume this is a 'parted' or an lvm issue - it did not effect final performance.

These partitions were then linked in lvm as a single 20TB JFS partition mounted inside of the root file system. (JFS because e2fsprogs doesn't handle creation of ext4 drives larger than 16TB... still... more than a year after listing this as a 'top priority'.)

Installation then proceeded as expected, but note that _**grub-install uses the wrong drive**_. Specifically, grub-install (as executed by the install script) was installing grub on to /dev/cciss/c0d0, I assume because it was detecting that drive as hd(0). Because the p400 was addressed as /dev/cciss/c1d0 and was also set as the boot controller, grub was sent to the wrong drive, and thus the explanation for the "Illegal Opcode" error on boot.

The Fix:

(First I should mention that right before fixing the issue, we also updated all the firmware on the server at HP Support's suggestion. I cannot rule out that this did not cause the success, although I personally feel it did not make the difference.)

As the *very last* step, when the install script ejects the install CD and asks you to press enter to reboot, _do not press enter_, and instead press alt+F2 to go to the install CD console. This screen should say "press enter to use this console" or something like that. Press enter, and use the following commands:

```

# chroot ./target
# grub-install /dev/cciss/c1d0

```

A large volume of text will scroll across the screen including a lot of what looks like bad errors - don't worry, this is just grub polling devices that don't exist. I think you can use something like "--no-floppy" to suppress those warnings, but don't worry about it. The last message should be "Installation successful" or something like that - that is your indication that the grub-install succeeded.

Press alt+f1 to return to the install script and press enter to reboot the machine. Your ProLiant DL580 with p800 raid controller should now boot without an illegal opcode exception.

---

