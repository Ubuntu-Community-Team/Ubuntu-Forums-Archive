---
title: "Installer needs to change partition table and should not!"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-01-16
Daily build for today installing from a CD Image in a partition fails because it is trying to change the partition table.  DON'T DO THAT!.  The  partition being installed to is already formatted by gparted.  NO PARTITION CHANGES ARE NEEDED!

Installer stops with the following message:

------------------------------------------------------------------------

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

-------------------------------------------------------------------------

On a quad boot system, the installer should not make any changes to any other partitions.  gparted doesn't have any trouble working with one partition leaving the others alone, the installer must be able to do the same.

Watch out!  A couple generations ago, was it Feisty Alpha, rewrote the entire partition tables on two hard drives blowing all my test (and backed up) partitions.

Yes, everything is backed up on this test system, but it does take a while to restore all the partitions.  this is launchpad bug #313452.

Jerry

---

### Post by LordVeovis on 2009-01-16
Have you submitted a bug?

Where did you get the daily at? I will try to reproduce on my laptop.

---

