---
title: "how do you set up a bootable software RAID1 using the 13.04 64-bit server install?"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by stiaszny2 on 2013-10-08
For years, I have booted from a software RAID1 using legacy grub and MBR partition tables.  This used to be extremely straightforward to set up using the ubuntu installer (either in the server install or the old "alternate" install if you wanted to create a desktop system running a RAID).  The old box died, and now I have a new box with EFI capabilities.  So now I am trying to do this using GRUB2 and a GPT partition table (I zero'ed my disks, so this was all done with the partitioner packaged with the 13.04 installer).  

The goal here is to have two *IDENTICAL* (as in, bit-for-bit) drives. (My test of installation success is to unplug the drives one at a time and all should be happy, except for the expected degraded RAID warning at boot-up).  I created the underlying partitions and RAID'ed them together, to end up with the following scheme, in order from the beginning of the drives:

100 MB which I set to EFI-boot
400 MB for /boot (formatted as ext3)
4 G       for /  (formatted as ext3)
8 G       for swap
1.4 T     for LVM (which I then use for my /home /tmp /usr and /var mounts)

At this point, the installer chokes with the error: 

"The attempt to mount a file system with type vfat in RAID1 device #0 at /boot/efi failed" 

I have found absolutely nothing about this error on the web, save for one page that mentions it in passing while advocating some stupid hackery involving making an un-RAIDed partition on one of the disks for the EFI partition.  Has anyone else even encountered this problem?

---

