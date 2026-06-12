---
title: "ISO fine on boot CD,yet can't boot Ubuntu"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by segorese on 2005-05-30
Title says it all.  I have the drive properly partitioned to accept Ubuntu, ISO written to a CD with a bootable sector and it still won't boot with Ctrl, Shift, or Del held down while booting (Del causes entry into the BIOS).

My machine's literature says nothing about "Large Byte Addressing" on the hard drive.

What am I still lacking, not doing, missing or otherwise?

segorese

---

### Post by mingus on 2005-05-30
Have you double-checked the usual suspects first? . . .

- BIOS is setup to boot from CD (you should see something like "press any key to boot from CD")?
- Did you press "any key" at the necessary time?  (It will bypass in a few seconds if you don't press a key.)
- Have you tested CD boot on another piece of bootable media?
- You used "burn image" and pointed to the ISO in whatever you used to create the CD?  (A bootable sector in and of itself does not guarantee this particular media will boot.)

Assuming you don't have another box to test the boot CD?

Why the ref to LBA?  LBA only *may* be a factor later with the boot loader you install.  As long as the HDD is properly recognized & configured in the BIOS, not a consideration now.  But on second thought, hmm . . .

By chance, do you have one of those big-ass drives that exceeds the BIOS or OS limitation, and so you installed a boot overlay?  I've seen an overlay grab the BIOS handoff, and also a corrupted overlay result in the HDD not being seen at all and stopping the boot cycle.  This probably isn't the case, but if it is, you'll probably have to get rid of the overlay.  Mine wasn't supported under Linux, and it didn't matter anyway because Linux doesn't care about geometries (but this will force you to use lilo with LBA rather than grub). 

Your partitioning scheme is also not relevant at this point.

---

