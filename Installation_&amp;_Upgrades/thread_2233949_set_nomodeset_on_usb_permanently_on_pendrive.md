---
title: "set nomodeset on usb permanently on pendrive"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by nutmegkel on 2014-07-11
can somebody help me to permantly se no modeset on my usb pendrive so don't have manually set it each time i start my laptop. Much love thanks

---

### Post by deadflowr on 2014-07-11
For persistence USB I gather?

Add the entry to 
/etc/default/grub
look for the line
GRUB_CMDLINE_LINUX_DEFAULT=
usually it will have an entry for quiet splash, add nomodeset to this line
like so
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
save.
This must be done as root/sudo.
and then, of course update grub
```
sudo update-grub
```

---

### Post by oldfred on 2014-07-11
If a full install then deadflower's instructions are correct. 

But if a live installer:

If UEFI the live installer boots with grub, but is not updateable.
But in BIOS mode the live installer boots with syslinux.

If booting with BIOS:
If you look in this you should also see the quiet splash similar to grub config file as mentioned by deadflower. 
Add nomodeset after quiet splash.
/isolinux/txt.cfg

If UEFI, not sure which is used:
/boot/grub/grub.cfg
/boot/grub/loopback.cfg
You may have to experiment.

---

