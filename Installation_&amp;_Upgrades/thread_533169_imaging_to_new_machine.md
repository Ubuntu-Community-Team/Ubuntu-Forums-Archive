---
title: "imaging to new machine"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by eisublime on 2007-08-23
I've got an Ubuntu 6.06.1 setup that I'm trying to image onto another
machine with identical hardware.  I was able to take an image of the
machine no problem but can't restore it to another machine.  I'm using
SystemRescueCD, and I'm having a hard time getting partimage to see my
partitions.  I've tried the following:

  creating new partitions using fdisk - partimage does not see the
partitions at all.  when I run partimage, at the top where the
partitions are supposed to be, there is nothing.

  creating new partitions using parted then setting one partition to
be the boot partition using fdisk - partimage sees the partitions,
images the partition, but then the machine doesn't boot

  copying the mbr from the source - dd if=/dev/cciss/c0d0 of=backup-
cciss.mbr count=1 bs=512; dd if=backup-cciss.mbr of=/dev/cciss/c0d0 -
doing this, fdisk sees the partitions, but diskpart does not.

Any ideas on what I may be doing wrong?

Thanks!

---

### Post by Pumalite on 2007-08-23
I don't know if it will help you, but I can contribute with this:
[http://www.novell.com/coolsolutions/feature/19486.html](http://www.novell.com/coolsolutions/feature/19486.html)

---

