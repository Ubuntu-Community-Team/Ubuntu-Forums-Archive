---
title: "2 Harddisks, cannot select boot"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by Bllz on 2007-11-28
Hey guys,
I have a computer with a 160 GB SATA drive, and a 20 GB IDE drive.  The IDE drive is installed as a slave drive on the second slot of the ribbon connecting to my optical drive -- it's the only way it would fit, and so far, there have been no problems.

I actually think the problem here is GRUB-related.

I have XP installed on the SATA drive, and that's what my computer boots to by default.  I booted from the Ubuntu Gutsy CD and installed Gutsy to the IDE drive.

Now obviously there's no way to select which device to boot from, so is there a way I can do this without harming my XP installation?

Thanks,
Bllz

---

### Post by dabl on 2007-11-28
You don't say where you installed Grub at the conclusion of the installation process -- hopefully you know.  Anyway, here is some useful guidance:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by Pumalite on 2007-11-28
It would be better for you to resize XP partition in your SATA drive and install Ubuntu there. Use Gparted Live CD. Use your IDE for storage.

---

### Post by Bllz on 2007-11-28
GRUB is located on the 20GIG IDE drive, or so I assume.  When I ran the install wizard on the live CD, I just selected the 20GIG IDE as the drive to which ubuntu should install.

Clearly that's not going to work, so is there a safe way to resize my SATA partition and then install GRUB there?  I'd rather confine Ubuntu to the IDE disk.

---

### Post by Pumalite on 2007-11-29
Use Gparted Live CD and resize your XP partition. Then install Ubuntu.

---

### Post by Bllz on 2007-12-02
Sounds doable.  Just to be clear though, how much space should I leave at the beginning of the SATA drive?  Will installing Ubuntu automatically install grub to the empty space in the SATA drive?

Sorry if I'm asking obvious questions...

---

