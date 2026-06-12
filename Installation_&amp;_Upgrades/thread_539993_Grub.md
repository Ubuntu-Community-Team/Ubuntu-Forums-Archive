---
title: "Grub"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-08-31
I recently installed openSUSE, and its version of grub now dominates my computer. Is there a way that I can get back the Ubuntu grub? Thanks.

---

### Post by be4truth on 2007-09-01
I assume you have Windows, Suse and Ubuntu installed. I assume you installed Suse after Ubuntu. I assume you can boot into all os. Is that right?
If so make sure that the entries in Suse /boot/grub/menu.lst are the same like in Ubuntu /boot/grub/menu.lst
If so, boot into Ubuntu and open a terminal:

```
grub-install /dev/hda or sda
```

Where hda or sda is the drive where the boot loader should be installed. This command will reinstall grub boot loader from your Ubuntu installation.
Make sure you have a backup of your data. Playing around with grub sometimes leads to unbootable systems if the player don't know the rules exactly.

---

