---
title: "Installing Ubuntu server with LSI 9211 RAID card"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by bennie2 on 2014-04-15
Hi There

I am at my wits end with this.

I am trying to install Ubuntu Server (12.04 OR 13.10 - makes no difference)  onto a 36bay supermicro server with an LSI 9211 8 port RAID card.

The Disks are configured to be JBODs - when booting the CD The first weird thing I notice is that there is no /dev/sda device, it starts with /dev/sdb and ends at /dev/sdak - /dev/sdb is a 500GB disk configured to be hd 0,0,0 ( so you would think it would show up as /dev/sda) that I want to install the OS to. All the other disks are completely blank, no partitions or anything.

I run through the installation and when prompted to install the grub bootloader I install it to /dev/sdb

After rebooting I am presented with just a blinking cursor, no grub boot menu. Even when specifically selecting the 500GB disk to boot via Boot Menu

If I boot the installation CD and select the "Boor from Hard Disk" option - I get "Booting from local disk..." and the same blinking cursor

In the BIOS the RAID adapter is configured to be AHCI mode - changing it to IDE or RAID makes no difference.

The 500GB disk is also set to be marked bootable in my raid card configuration manager.

If I boot a live disk I can mount and chroot my 500GB disk and see all the installed files.


Please, halp

---

