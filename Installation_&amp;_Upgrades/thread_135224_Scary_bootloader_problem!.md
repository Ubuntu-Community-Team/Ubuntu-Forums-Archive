---
title: "Scary bootloader problem!"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by Qwertie on 2006-02-23
I have two hard drives, a 'regular' 80gig drive and a 200gig SATA drive.  I attempted to install Kubuntu on the 200gig drive, which already had a working Windows 2000 installation.  Everything seemed to go fine until I rebooted after the "first stage is complete".  The 200gig drive is set in the BIOS as my boot device and I'm getting the following error message: "Error loading operating system."

It asked me if I wanted to install GRUB and I said yes, but I noticed that it said it detected all four operating systems, including two from the 80gig drive.  Hmmm.

---

### Post by Qwertie on 2006-02-23
Okay, as I suspected, Kubuntu has replaced the bootloader on the wrong hard drive, and somehow made the 200gig drive nonbootable.  Craptastic!

How do I fix both drives?  How do I get GRUB onto the 200gig drive, and preferably, how do I get both drives to just boot what is on them rather than what is on the other drives?

---

