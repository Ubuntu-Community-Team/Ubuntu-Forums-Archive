---
title: "migrate Gusty to USB HDD"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by maxalken on 2007-11-02
I am trying to boot Gusty from an encrypted USB HDD, but it does not work.

I have installed Gusty on my laptop with whole disk encrypted and it is working fine. I have copied this system to an external USB HDD and made a new initrd image in the chroot environment on the USB HDD with **update-initramfs -u**. I have made the following changes before making the new initrd image:
[LIST]
[*]changed all (hd0,0) to (hd1,0) in /boot/grub/menu.lst
[*]replaced the UUID of sda5 to sdb5 in /etc/crypttab
[*]replaced the UUID of the swap logical volume to the UUID of the swap logical volume on the USB HDD in /etc/initramfs-tools/conf.d/resume
[/LIST]

when I typed **update-initramfs -u** it complained:
> update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
cryptsetup: WARNING: invalid line in /etc/crypttab - 
cryptsetup: WARNING: invalid line in /etc/crypttab - 

I have these in */etc/initramfs-tools/modules*
> ehci-hcd
usb-storage
scsi_mod
sd_mod


When I boot from the USB HDD, the system stopped at the splash screen. Does anyone know what I did wrong?

---

