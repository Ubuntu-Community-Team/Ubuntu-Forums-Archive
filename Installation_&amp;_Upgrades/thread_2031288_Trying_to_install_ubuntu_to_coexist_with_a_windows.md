---
title: "Trying to install ubuntu to coexist with a windows 7 installation"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by Rock` on 2012-07-21
They are on separate hard drives. Every time I try to install Ubuntu, everything goes smoothly, I remove my USB stick, reboot and it boots straight into Windows without giving me the option to boot into Ubuntu. Most likely a problem with GRUB not being configured correctly. Any idea on what I can do?

---

### Post by kestrel1 on 2012-07-21
Doesn't sound like grub is on the first bootable hard drive.
Go in to your BIOS & set the other HDD as the primary bootable drive & see what happens.

---

### Post by darkod on 2012-07-21
Also, when installing from usb sometimes it can consider the stick as the main boot device (since you booted from it for the install), so grub2 can end up there.

First try without the stick, go into BIOS and set it to boot from the other internal disk.

If that doesn't work, try it with the stick and boot from the usb. See if that will give you the bootable usb stick menu, of the grub2 with the dual boot options you are suppored to have.

If it does work with the stick, boot ubuntu once and install grub2 to the disk you want (/dev/sda or /dev/sdb, depends) with:
sudo grub-install /dev/sdX

But you can do that only if you manage to boot the hdd ubuntu, I am not talking about the live desktop.

---

