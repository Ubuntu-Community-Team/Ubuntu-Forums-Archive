---
title: "How to restore a complete system from a backup?"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2010-09-17
Hi,

I have a normal Ubuntu 10.4 server setup with RAID-1 and LVM, where /boot is on /dev/md0 and / is on /dev/vg0/root. I backed all files with duplicity. Now I am running a rescue system where I can create all partitions, RAID, LVM and stuff, mount it all to /mnt resp. /mnt/boot and then restore all files using duplicity. All files should now be there. But there's no bootloader in the MBR.

When I reboot the system, it hangs at boot and says "ALERT! /dev/mapper/vg0-root does not exist. Dropping to a shell!". In /dev/mapper the only thing that exists is "control". No LVM commands are available to look around.

I have taken the following steps after file restoration to try and install the bootloader on the disks: (all in the chrooted restored system)

* Run 'grub-setup /dev/sda' and 'grub-setup /dev/sdb'
* Reinstall the package grub-pc
* Reinstall the package linux-image-2.6.32-23-server

All of them reported success or remained silent. Looking at the MBR with 'less -f /dev/sda' (or dd and hexdump) showed some good looking data there. (Before the restoration I erased the first 400 MB of the disks with /dev/zero.)

So why doesn't the system boot anymore after restore? How is a full system backup meant to be restored on Ubuntu Server?

Edit: I have now found the lvm command in the BusyBox, but running vgscan and other stuff in it doesn't find any LVM groups or volumes at all. When I reboot to the rescue system, the LVM volumes work just fine though!

---

