---
title: "Cloning boot SATA HD to a USB flash drive"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by maduro on 2009-11-27
Hi,

I have a working 9.04 on an internal SATA drive and everything is humming along just fine.  I've done custom setup on the OS for various applications.  What I'd like to do is to migrate everything to an 8GB USB flash drive and pull out the hard drive.  I was thinking of using Clonezilla to migrate the partitions.

Has anyone such a thing and what are the challenges?  TIA.

maduro

---

### Post by lemming465 on 2009-11-28
I've done disk to disk migrations before successfully, though typically with other Linux distributions, rather than Ubuntu.  It's definitely feasible; this is how the Ubuntu live-CD installer Ubiquity works, after all. The main two things with Ubuntu to watch out for are fstab and the bootloader.  You may find it easiest to do the copy using a live CD so that you don't have so many mounts to deal with on the SATA root partition.  If you have ACL's or SeLinux labels do the copy with *star*, which is not installed by default.  If you have encrypted home directories I'd definitely suggest doing the clone using either a live CD or a special admin user with an unencrypted home directory you create just for that purpose.

Most Ubuntu partitions are mounted by UUID, not by device.  After doing *mkfs -t ext4* and *mkswap* on the USB drive partitions be sure to run *blkid* and adjust the cloned /etc/fstab to match the new UUID's.

Also, you'll need to run *grub-install --root-directory=...* to put a boot loader on the USB device.

---

### Post by phillw on 2009-11-28
cpio is pretty darn good at 'photo-copying' dissimilar file-systems as it does not depend on block size, etc.

dd can do block size conversions (as its name says (dd == Copy And Convert - It's a *nix thing, as CC stands for C Compiler)

Regards,

phill.

---

