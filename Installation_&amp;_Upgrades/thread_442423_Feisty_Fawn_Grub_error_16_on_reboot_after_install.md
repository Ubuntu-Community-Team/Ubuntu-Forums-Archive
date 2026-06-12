---
title: "Feisty Fawn: Grub error 16 on reboot after install"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by DoctorOwl on 2007-05-13
Here's my setup.  P4 2.2 on an old Intel D850MV motherboard with standard IDE ports.
IDE0 - HDD0 - XP SP 2 on NTFS
IDE0 - HDD1 - NTFS Data
IDE1 - HDD0 - Empty HDD for Ubuntu
IDE1 - HDD1 - DVD-RW

I booted the Ubuntu 7.04 CD and allowed it to install to IDE1 HDD0.  It then installed Grub to IDE0 HDD0.

On reboot Grub gets to Stage 1.5 and gives an Error 16 and hangs.  Note that at that stage there are no options to select or anything you can do except reboot.

I was able to boot from the XP CD and FIXMBR and FIXBOOT so I could access XP again.  Which means one of two things:

- either Grub doesn't handle booting IDE1 HDD0 even if it has the MBR on IDE0 HDD0, and Ubuntu shouldn't let you install it like that.
or
- there is some easy solution here that should have been thought of beforehand and put into the installer.

Can someone shed some light here?  Maybe I should email the Grub developer?

Cheers
DoctorOwl

---

