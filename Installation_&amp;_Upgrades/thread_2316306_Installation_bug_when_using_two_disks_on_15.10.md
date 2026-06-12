---
title: "Installation bug when using two disks on 15.10?"
date: 2016-03-07
forum: Installation &amp; Upgrades
---

### Post by Bill_Hensley on 2016-03-07
Hi, I have an HP 6970b laptop.  It came with a disk with Windows 7 (which would be /dev/sda).

I decided to use Ubuntu to experiment with VMs.  I installed a second disk in the machine in place of the DVD (which is /dev/sdb).  I then downloaded Ubuntu 15.10, got it on a USB stick, rebooted the machine off the USB stick, and pointed the installation at the new drive (/dev/sdb).  Installation seemed to go well and I could boot Ubuntu without any issue.  

However... I noted very briefly during the install that GRUB was installed on /dev/sda.  I never saw any option to not let that happen.  The upshot is that my Windows 7, which was on a physically separate disk, is trashed now, unbootable.  I am going to pull the disk and see if I can mount it via USB on another windows machine.  

I think this is a bug in Ubuntu.  When I pointed it at /dev/sdb, it should not have written anything to /dev/sda.  Did I miss a configuration setting?  Is this something UEFI related?

I have dual-booted numerous machines, and I remember that I would always install Linux SECOND since Windows always trashed any previous Linux install.  I think this is first time Linux has trashed an existing OS.

Any advice would be appreciated.

Cheers, Bill

---

