---
title: "Installing Ubuntu on an External Drive"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by rfbeck on 2010-03-25
I wish to install Ubuntu in a dual boot configuration on my laptop. I want Windows 7 to remain on my laptop's hard drive, and Ubuntu to be on my external drive. Is this possible? If it is, will my external drive always have to be connected in order to just start Win7 ? 
Thanks.
______
Robert

---

### Post by kooia on 2010-03-25
No, but Ubuntu gives you the option to run it on a CD.

However, you can buy another hard drive, and attach it via the SATA/ATA ports.  Then you can run Ubuntu on that.  Although, I don't know how this would work.  You might have to change the BIOS every time you want to change.

Is this because you don't want to have your disk filled up?  If it is, I suggest getting a RAID controller.  Then you can run a few hard drives together, with your computer treating it as one.  That's how Fabrice Bellard got a 7.5TB disk for calculating Pi.

I actually don't have any idea how to set it up, although SATA is a PCI chip that makes the computer think multiple hard drives are one.  Ask somewhere else what that is.. maybe yahoo! answers.

---

### Post by bumanie on 2010-03-25
As long as at the partitioning stage you choose "advanced" and ensure grub is installed to the external hard drive, you won't have problems with grub being on the mbr of the windows (internal) hard drive. When i have done this in th past, I have had to modify grub on the external hard drive to be (hd0,0) after the installation, so that it will boot when bios is set to boot from usb hdd. I have **not tried** this with **grub 2** as yet, so I can't tell you what to do with grub 2's /boot/grub/grub.cfg file. I am sure it would be mentioned on a grub 2 tutorial. Guess I should try this myself sometime soon.

---

