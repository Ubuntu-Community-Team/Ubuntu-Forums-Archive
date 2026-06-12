---
title: "Just installed 14.04.4 and it won't boot."
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2016-03-04
***Newb warning - limited Linux knowledge ***

I just install Trusty Tahr on to my Intel Atom based machine.  Install appeared to complete just fine, but nothing happens on boot.  Just a blank screen with the cursor about 3 lines from the top.  The graphics is an integrated Intel GMA 3150 ( GMA3150 ) .  I don't believe that Grub is being loaded.   

This install was to an SSD in AHCI mode, and I chose Guided with LVM installation.  The partition layout shown in GParted is:

/dev/sdb1    ext2                    243.00 MiB etc.
/dev/sdb2    extended                 89.19 GiB
  /dev/sdb5  lvm2 pv    Charon-vg     89.18 GiB

None of the partitions are marked bootable.

/dev/sda is empty and intended to be a storage volume and is attached to RAID card.

How can I persaude this to boot please?

Thanks
Dave

---

### Post by grahammechanical on 2016-03-04
Where was Grub installed? To which drive? The default is to sda but Ubuntu is installed on to sdb. If the motherboard is looking to sdb for a boot loader, then it is not going to find one if the boot loader is on sda.

If Ubuntu is the only OS then we will not see a Grub boot menu. It is still there trying to do its job of loading the only OS but it does not show itself. Press Shift a few times at an early part of the boot process. That should bring up Grub.

.See, where that gets you,

Regards.

---

### Post by David_Partridge on 2016-03-04
Sounds like a good reason for it not booting.  As the Server install CD didn't offer a "reinstalll Grub" option, is disconnected the drive attached the RAID controller, and re-ran the install.

All worked as expected this time, and continued to do so after reattaching the storage drive to the RAID.

Now back to that learning cliff.

Cheers
Dave

---

