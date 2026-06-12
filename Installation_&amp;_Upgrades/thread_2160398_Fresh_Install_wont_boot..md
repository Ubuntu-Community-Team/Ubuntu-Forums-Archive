---
title: "Fresh Install wont boot."
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by leotemp on 2013-07-06
Made a USB install drive for Ubuntu 13.04, after running a complete drive wipe ubuntu only installation i restart and get an error "reboot and select proper boot device" as the HD wont boot. If i load up the usb live cd and gparted i see grub is on a partition marked "/boot" i have another "/" and swap. I've tried reinstalling a dozen times with as many different configurations from other help threads but no matter what i cannot seem to get grub to boot my successfully installed Ubuntu system.

---

### Post by DeathByDenim on 2013-07-06
You could try going into the BIOS and fiddle with the boot order. Does the computer boot when you put the hard drive on the first position in the boot order?

---

### Post by fantab on 2013-07-07
Have you disconnected the USB when you are booting Ubuntu? If yes, then check in your BIOS HDD boot order/priority, it must be set to boot your HDD with Ubuntu First.

---

