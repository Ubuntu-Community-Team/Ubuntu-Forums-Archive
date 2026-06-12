---
title: "Installation from flash drive..."
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by modmadmike on 2010-06-28
I have a complete install (Ext4 / and a FAT16 /boot partitions) on an 8gb flash-drive to repair computers. The install was done without the USB creator for various reasons (I needed to have a complete system on a flash-drive). Because it is a regular install I have no icon to install it on the host's HDD. I saw a guide a while back to put the installer on an actual installation, but it is outdated and I cannot find it anymore. Any tips? (besides using the USB creator). I am adept with the command line (and gnome), but don't know much about the SquashFS filesystem on the install CD.

---

### Post by darkod on 2010-06-28
You probably have grub1 or grub2 on the flash right now to boot the system.
How about simply unpacking the ISO inside a separate folder, and just adding a title in the current boot menu to kick off the installer? If you can spare 700MB space on the flash.

Maybe it's not the best solution, but it should work for sure.

---

### Post by C.S.Cameron on 2010-06-28
You can clone or copy what is on your flash drive to a HDD but would have to boot from a third drive to do so.

---

