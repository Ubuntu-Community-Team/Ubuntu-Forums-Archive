---
title: "Installing over another distro on partitioned drive"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by schwim on 2009-11-14
Hi there everyone,

I'm considering replacing my Dreamlinux(Debian) install on my laptop 9.10.  Currently, DL shares space with XP on this machine.  I've never changed distros on a dualboot machine and I'm wondering if I'll be able to simply pop in the disc, choose the DL partition and that's it or if I have to do something to get Ubuntu to keep XP in the boot menu.

I'm googling, but everything I find so far is in regards to dualbooting for an initial install, not for upgrading a machine that's already dualbooted.

Thanks for your time,
json

---

### Post by Jose Catre-Vandis on 2009-11-14
You will need to choose "Manual" when in the Partitioner and select the correct partition to overwrite (so that you don't wipe Windows!). Boot a Live CD and run gparted to correctly identify partitions.

Alternately, you could use gparted to remove all partitions you do not want, leaving unallocated space, and then let Ubuntu use the unallocated space when you install.

Ubuntu should be allowed to write grub2 to the mbr (this happens by default) and Windows will/should be in the new grub menu.

---

### Post by schwim on 2009-11-15
Thanks very much for your help.  Installed without a hitch.

thanks,
json

---

### Post by Jose Catre-Vandis on 2009-11-16
:)

---

