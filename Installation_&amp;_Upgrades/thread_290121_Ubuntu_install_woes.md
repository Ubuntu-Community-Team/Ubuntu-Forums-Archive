---
title: "Ubuntu install woes"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by mga on 2006-10-31
I'm having some difficulty with my Ubuntu install, in two parts.

**1. Ubuntu**
I've got a new 320GB IDE disk on which I'm happy to give up to 10-20GB for Ubuntu, but want the rest for storage (also accessible from Windows). I tried setting up suitable partitions on the drive from Windows (two 4GB partitions for the system and for scratch, at the outer edge of the drive) and then booted the Ubuntu CD installer, but it wouldn't install

Instead, I erased the whole disk and let Ubuntu partition however it saw fit. This has allowed it to install. The problem now is, I can't access any of the 320GB from Windows.

How can I install Ubuntu such that it takes up <20GB and I get a 300GB NTFS partition for use in Windows? Can I do this with the Ubuntu installer, or do I have to set up my disk before beginning the install?

**2. GRUB**
I've also got an IDE Windows disk and a SATA Windows disk on my system (via the Asus A7N8X Deluxe's onboard onboard SiI 3112r SATA controller).

GRUB can see the IDE Windows install, but when I try to boot it nothing happens - I just get a blank screen. GRUB can't see the SATA drive at all. How can I fix this?

---

### Post by DaveBorealis on 2006-10-31
> **mga said:**
> Instead, I erased the whole disk and let Ubuntu partition however it saw fit. This has allowed it to install. The problem now is, I can't access any of the 320GB from Windows.

Hello,

Reinstall Ubuntu, but this time make a 10 Gig primary partition ext3 for root, '/', and whatever for your swap (probably a Gig or less), then make the rest into a third, vfat32 primary partition.  Widows should now see that third partition.

Best regards,
Dave

---

### Post by xp_newbie on 2006-10-31
Yes, you can do it with the Ubuntu installer. When the installation wizard takes you to the page that asks you for the method to setup your hard drive, choose option #3 - the **manual** option.

Never select option #2 (automatic) - it is buggy and ruined my HDD once.

Good luck!
Alex

P.S. The partition you want to be accessible from windows, needs to be:
     1. Either set and formatted as NTFS.
     2. Set it ext3 (like the rest of Ubuntu) and install an [ext3 FS driver for Windows]("http://www.fs-driver.org/").

---

### Post by mga on 2006-11-02
Thanks, I've got the install how I want it now.

Still having problems with the bootloader though!

---

