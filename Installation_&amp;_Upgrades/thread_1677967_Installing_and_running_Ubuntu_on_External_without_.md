---
title: "Installing and running Ubuntu on External without GRUB?"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by hooless on 2011-01-29
Hey, the thread says it all; I was interested if I could run Ubuntu off of my external hard drive, but without having to install GRUB on my laptop, because it is such a pain getting it off (Windows recovery disk and all that)...

So I hope there's a way to install and run it without having to install GRUB or if there's actually an easier way to remove if I choose to without having to "nuke" my computer... thanks!

---

### Post by ajgreeny on 2011-01-29
Yes, you can use the **Advanced** button in the installation process to put grub on the USB, which might be /dev/sdb, but will depend on your system, and the disks already in it.
I can't remember where that button appears in the latest ubuntu; it used to be on the final screen, but is now earlier, I think, perhaps on the partitioning screen, and I think it only appears if you choose the manual partitioning option.

Once installed in that manner, you set the USB as first boot device, hard disk as second, so that the USB boots if attached, but if not the windows disk boots straight to windows.

---

### Post by hooless on 2011-01-29
> **ajgreeny said:**
> Yes, you can use the **Advanced** button in the installation process to put grub on the USB, which might be /dev/sdb, but will depend on your system, and the disks already in it.
I can't remember where that button appears in the latest ubuntu; it used to be on the final screen, but is now earlier, I think, perhaps on the partitioning screen, and I think it only appears if you choose the manual partitioning option.

Once installed in that manner, you set the USB as first boot device, hard disk as second, so that the USB boots if attached, but if not the windows disk boots straight to windows.

Sweet! That sounds like it will work! Just curious; I would just have to reformat that partition in order to get GRUB off, I wouldn't have to reformat to entire disk right?

---

### Post by ajgreeny on 2011-01-30
Sorry, but I don't understand your question; get grub off what?

You install ubuntu on to the partitions on the USB, and put grub on the first block of the disk, not on a partition, ie, on /dev/sdb without a final partition number.

---

### Post by ashickur.noor on 2011-01-30
I think You don't need to install. Use startup Disk creator to make your usb stick bootable.

---

### Post by P4man on 2011-01-30
> **hooless said:**
> Sweet! That sounds like it will work! Just curious; I would just have to reformat that partition in order to get GRUB off, I wouldn't have to reformat to entire disk right?

No. All you have to do is boot the windows CD and run FIXBOOT (depending on version of windows, fixboot is for XP I think). That will overwrite the grub bootloader with the windows bootloader.

---

