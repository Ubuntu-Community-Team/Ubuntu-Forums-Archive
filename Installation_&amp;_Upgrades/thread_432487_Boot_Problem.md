---
title: "Boot Problem"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by _simon_ on 2007-05-04
I am installing Ubuntu 7.04 as a dual boot alongside XP MCE for my partners dad on his new machine.

The install seems to have gone fine, in that I did not get any error messages and was told to reboot the machine.
On rebooting, I am faced with a "no boot device detected - press any key to continue"

I've tried disabling every boot device except the hard drive and still get the message.

It does not even appear to load grub, even though I watched it being installed.

Where should I go from here?

It's a 120Gb drive split as follows:

hda1 - 55.64 NTFS (Xp MCE Install) (boot)
hda2 - 4.62 FAT32 (Recovery Partition)
hda3 - 50.28 EXT3 (Ubuntu Install) (boot)
had4 - 1.25 - Extended
hda5 - 1.25 Linux-Swap

I'm not sure if the NTFS AND EXT3 should both be boot? If not, which one shouldn't and how do I remove the flag?

---

### Post by _simon_ on 2007-05-04
Fixed.

Not sure what happened.

Used gparted to delete the partitions, made 2 new ones and ran the install again, it now works as it should.

---

