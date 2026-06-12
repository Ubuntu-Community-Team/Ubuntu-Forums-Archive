---
title: "Dapper failed to install, or missing bootloader?"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by jgreath on 2006-07-10
First off, hi everyone!

I've been a fan of Ubuntu for a while now, and was interested in trying the latest version (Dapper) on my desktop.  I recently purchased my first SATA disk, and decided to make it my "OS disk" since it should provide improved performance over the PATA drives I had been using.  I installed XP on it, and that went just fine.  I then inserted the Dapper LiveCD and followed the installation instructions.  After removing the CD and rebooting, I'm just thrown right back into Windows.  No GRUB menu, no visible bootloader menu of any kind, just Windows.

So, did Dapper fail to install?  Or did Dapper fail to install GRUB?  Could GRUB have been installed to my PATA disk for some reason?  Are there any limitations in GRUB as far as SATA drives are concerned?  It's a single SATA drive, so it isn't a RAID array or anything at all complicated.

I'm using an Athlon 64 3200+ with an ECS RX480-A ATI XPRESS 200 motherboard, GeForce 7600GS (PCIe) graphics card, and an Atheros-based WiFi card.  The SATA disk and the PATA disk are both from Seagate.  My DVD-RW drive is from BenQ.  If any other system specifications would help, just let me know.

---

### Post by jgreath on 2006-07-10
Okay, I found the answer.  The Dapper installer placed GRUB on the PATA disk, even though Ubuntu is installed on the SATA disk (which is the only disk set in the BIOS to be booted).  Can I just install GRUB on the SATA drive without screwing up my system, or will GRUB not get along with SATA?

---

### Post by scxtt on 2006-07-10
that's really odd, grub installed fine on my SATA disk (/dev/sda1, as if i had a choice :p) - i have 2 of them, unRAIDed ... you could just boot grub off the PATA (leave it as default in BIOS) then select which SATA partition to boot ... unless you're removing the PATA disk ...

---

### Post by Akula on 2006-07-11
I had same problem (SATA disk as master and PATA as slave). I quess my ubuntu install (Ubuntu is on PATA disk, windows is on SATA) did install grub on PATA disk, as my computer booted to windows without any menus.

I corrected the problem by using grub bootdisk (or was it system rescue cd...) and installing grub to SATA drive myself (used find to make sure which drive was ubuntu drive(PATA) and to make sure that I don't install grub on PATA again). 

Even after I got grub menu to show up on SATA, it did not work right. I had to modify menu.lst settings to change hds for example hd0 -> hd1 and hd1 -> hd0. ( I don't know if you have to do this at all. )

Looks like that when using grub bootdisk, SATA disk was hd1 and PATA disk was hd0. When booting normally it was the opposite. I'm not sure how the install saw it.

---

### Post by jgreath on 2006-07-11
My computer's BIOS lists all the disks as IDE drives, even the SATA drives (I assume it just reports them as IDE so that Windows won't bitch about installing there).  Anyway, a possible cause of GRUB going to the PATA drive is that the two PATA channels are listed as IDE channels 1 and 2, with the remaining SATA channels listed as 3 and 4.  Perhaps GRUB picks the first drive in the list, which would have been the first disk on the first channel (which is the PATA disk).

Actually, Windows did the same thing.  I installed to the SATA, but it marked the PATA drive as the "System" disk and refused to boot after I took it out.  So I just took the drive out and reinstalled Windows.

I'll just reinstall GRUB on the SATA disk myself, but perhaps that should be a future feature addition to the Ubuntu installer: allowing the user to select which disk to install GRUB to, or installing GRUB to the same disk that Ubuntu is installed to.

---

