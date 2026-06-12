---
title: "updating packages on USB Startup disk?"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2010-03-06
So i created a USB startup disk on my 32g flash.  Worked fine until I went to update the packages on it.  Now it wont boot up and it also fails when trying to install on another machine.

Where should I start looking for problems on a USB OS?

---

### Post by efflandt on 2010-03-06
Existing packages from the iso are in a fixed squashfs filesystem which boots up before persistent data is mounted.  You can add packages, but updating packages is not a good idea (especially the kernel, which loads before anything else anyway).

There have been posts explaining how to make changes to existing files in the iso or on the USB itself.

But if you really want a secure updated system on USB, it should probably be a regular installation, instead of just a USB start up disk.  If you do that, pay attention to the Advance button to put grub on mbr of the USB (instead of default to your main hard drive).

And you may want to use tmpfs for /tmp like a USB startup disk does to minimize writing small temporary files to flash memory.  Example /etc/fstab entry:

tmpfs /tmp tmpfs nosuid,nodev 0 0

---

