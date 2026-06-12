---
title: "Update from Hoary to Breezy and Migration from ATA to SATA"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Scrambler on 2005-11-10
Hello,

I have an installed Hoary on an ATA disk which works great. Now I wanted to do an upgrade to Breezy (because of a lot of installed add-ons to Hoary) but before that, switch to a SATA disk. So I used a disk imaging program (Acronis) to make an image from my old ATA to the SATA and checked the partitions.

I then modified grub to boot from /dev/sda1 and changed /etc/fstab for the correct disk entries to mount and installed grub on that boot sector.

All I get upon boot though is a grub error message that there is a disk error and nothing else...

I did an Breezy installation with the removed ATA disk on the SATA disk and that works fine. But what I actually want is an update of my Hoary. Something that I have not yet succeeded with :-(

Can anybody help?! Thanks,

    Scrambler

---

