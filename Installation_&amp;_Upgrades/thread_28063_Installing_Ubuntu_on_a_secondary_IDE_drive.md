---
title: "Installing Ubuntu on a secondary IDE drive"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Dreamstar on 2005-04-18
Hi i have a SATA driver as primary HD with windows XP on it. 
I wish to install ubuntu on a secondary IDE drive, but after the install it looks like GRUB didn't install on my SATA drive coz when pc starts Windows is always loaded and no GRUB displayed
How can i do?
thanks

---

### Post by alastair on 2005-04-18
Not sure. Did Ubuntu see the SATA drive when you installed it?

You could always install GRUB on a floppy.

---

### Post by Curing@ on 2005-04-21
I have the same problem.  :???:

---

### Post by alastair on 2005-04-22
Actually, as a test for 64 bit-ness, I installed 5.04 on a Dell 670 yesterday. This has a SATA drive for Windows and I installed an IDE drive on primary master for Ubuntu (hda).

Not wanting to touch or worry about the SATA drive/XP, I tried to install GRUB on a floppy. This "worked" but didn't boot afterwards (just sat on "GRUB").

So, I installed GRUB (reinstall 5.04) on the IDE disk /dev/hda.

This now boots - but I have to boot OFF the IDE disk i.e. choose the boot disk at the BIOS screen, then I get the GRUB menu. I can't appear to boot XP from GRUB however (but not a big deal for me).

---

