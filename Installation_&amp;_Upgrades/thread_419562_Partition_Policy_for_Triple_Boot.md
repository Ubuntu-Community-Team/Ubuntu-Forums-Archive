---
title: "Partition Policy for Triple Boot?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Catsworth on 2007-04-23
Hey Guys,

Just after some advice please.

Have a laptop with a 40Gb HDD in it, I want to put Windows XP Pro, Ubuntu Fiesty Fawn, and a 3rd Linux distro on the same drive, with a partition so that the 3 can share data.

Any thoughts on the best partition setup for this?

Thanks,

*Cats*

---

### Post by BoneKracker on 2007-04-23
_I. One option:_

1. One partition for Windows.  15 GB
2. One partition for Linux A.     10 GB
3. One partition for Linux B.     10 GB
4. One shared data partition.    5 GB
[LIST]
[*]Designate 2 and 3 as physical volumes for LVM, and create one LVM volume group for each.
[*]Partition each of those two LVM volume groups as you wish, according to your needs for each Linux distribution.
[*](If you really want, you could leave out the swap partition on 3 and reuse the swap created on 2).
[*]Put the vfat filesystem on 4, so all three systems can safely access it (unless it's not important stuff, in which case you might use ntfs-3g).
[/LIST]

_II. A second option:_

1. One partition for Windows. 15 GB
2. One swap partition
3. One Linux extended partition containing:
    3.a Logical partition(s) for Linux A.
    3.b Logical partition(s) for Linux B.
4. One shared partition.

_III. As to the bootloade:r_
I would probably allow each system to maintain its own bootloader.  Install to the disk's MBR from the Linux you are least likely to uninstall (i.e., Linux A.).  In that bootloader configuration, chain-load Windows as well as the bootloader of Linux B.  (Rather than using one bootloader configuration file to define the bootlines (i.e., the "images") for both Linux A and B.)

---

