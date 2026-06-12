---
title: "Mirroring a machine with logical volumes"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by mohnkern on 2007-08-01
I've built one machine with a boot partition, and then logical volumes.

I'd like to "mirror" this onto another machine,  I created the two partitions (including the lvm partition) on the new machine, however I'm wondering if there's an easy way to export the lvm metadata from one machine to another, rather than having to put it into the new machine.

vgexport is used if you're just moving the drive from one machine to another, but I actually want to duplicate the data on a separate machine.

Anyone have any ideas?

---

### Post by mohnkern on 2007-08-01
I'm thinking the following may work, trying it:

On old machine:

vgexport -a

Then from new machine:
 ssh <oldmachine> "dd if=/dev/hda2" | dd of=/dev/hda2

When it's done type:

vgimport -a

on both boxes.

---

