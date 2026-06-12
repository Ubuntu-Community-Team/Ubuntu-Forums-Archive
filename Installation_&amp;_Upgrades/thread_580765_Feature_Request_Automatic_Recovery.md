---
title: "Feature Request: Automatic Recovery"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by daengbo on 2007-10-19
I would like to request a feature for Ubiquity: an option to place a copy of the live CD on the hard disk in the boot partition during installation, after which an entry is placed in Grub to boot from this disk image (In reality, mount the .iso as a loopback device and chroot into it).

Once the "restore" image is booted, the user could then use the live image to fix the problem or launch Ubiquity.  Ubiquity would have a new option to "Restore," backing up the old /home to an external device and then simply reinstalling the system. If a preseed file were written to the /boot partition during the original installation, there wouldn't need to be any user input at all outside of a password for the default user.

What do you think?

---

