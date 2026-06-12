---
title: "Can't install &quot;error: couldn't read file&quot;"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by sonnenwende93 on 2011-05-01
I have been trying to install 11.04 onto an external eSATA disk. This computer had Ubuntu installed two years ago on the internal HD, with no problems, but that disk is full now, and my only option is an external disk.

I have tried installing from the livecd after unplugging the internal disk and making sure that the eSATA disk is showing in the BIOS, but after installation I only received a grub error "couldn't read file." If I start from the recovery mode option, I eventually see this error: "kernel panic-not syncing VFS:unable to mount root fs on unknown-block(0,0)."

I booted into the CD and reinstalled grub (grub-install) and it did not make any change.

I also tried installing from wubi and on reboot got the same "couldn't read file" error.

Maybe there's something really simple I am overlooking?

---

### Post by sonnenwende93 on 2011-05-01
Hooked disk up via USB instead and formatted it, reinstalled from wubi, and rebooted and it appeared to load and configure everything, however on subsequent reboots when ubuntu is selected from the bootloader the computer just restarts.

---

