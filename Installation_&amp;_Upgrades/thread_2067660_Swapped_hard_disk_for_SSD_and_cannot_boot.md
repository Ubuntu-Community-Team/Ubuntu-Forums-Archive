---
title: "Swapped hard disk for SSD and cannot boot"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by madwoollything on 2012-10-07
I've recently installed a second hard disk (SSD) in place of my DVD on a laptop.

The SSD was not giving the speed that I expected and have now swapped the SATA hard disk with the SSD. I've used Super Grub2 to boot the system and I can access all the OSs and the SSD is running much faster.

The only problem is that I cannot seem to get the system to boot. I've rebuilt Grub and installed to both disks (as I'm unsure which the laptop will use to boot from). There does not appear to be any settings in the BIOS so I can set which disk the system uses for boot .... but this is a SATA based system???

How can I get my laptop booting again?

---

### Post by darkod on 2012-10-07
From other similar threads it seems the disk installed in the dvd bay is not seen as a hard disk during boot, so if the OS boot files are there, it doesn't look like it will boot from it.

You might have grub2 on the SSD but if all boot files for all OSs are on the HDD in the dvd bay, it can't call them from there.

At least that's my assumption from what I have seen.

---

