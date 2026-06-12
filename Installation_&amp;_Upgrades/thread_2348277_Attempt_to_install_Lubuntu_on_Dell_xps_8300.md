---
title: "Attempt to install Lubuntu on Dell xps 8300"
date: 2017-01-02
forum: Installation &amp; Upgrades
---

### Post by rccharles on 2017-01-02
I attempted to install Lubuntu 16.10 [ lubuntu-16.10-desktop-i386 ] on a Dell XPS 8300 computer. Some details:
-- Windows 7
-- attempting to set up a dual boot system
-- 1.5 Terabyte hd
-- 16 gig memory 
-- lots of space on the hd
-- looked like the partitions were set up ok.
-- from reading online articles, I believe the machine still uses bios

Failed.  Grub would not install.
"Sorry error occurred and it was not possible to install the boat loader at the specified location"

Questions behind the obvious how to fix.
1) How do I verify that the machine uses bios opposed to uefi?
2) How do I get more details on why grub failed to install. 

The machine is a friend's machine.  So, I'm interested in figuring out how to proceed the next time I visit. 

Robert

---

### Post by ubfan1 on 2017-01-02
On what location did you try and install grub?  The usual one would be sda.  First figure out what partitioning your disk uses.  Running fdisk or gdisk from the Ubuntu live media should tell you.  Another clue would be if you have an extended partition, that is sufficient to make it a DOS partitioned disk.  If you don't have an extended partition, and have more than four partitions, that means it's GPT partitioned.  Now a DOS disk should just accept sda as a location, but a GPT disk cannot, unless you have a tiny 1-2M partition with a grub-bios flag (for the rest of the bootloader).  Whatever mode Windows is installed in, Ubuntu should be installed the same way.  If your disk is DOS partitioned, Windows is in legacy mode.  Check the BIOS/UEFI settings for ways to select either legacy, or UEFI mode, or preferences which will boot in preference to the other -- The Ubuntu install media boot both ways, so you must use settings in the BIOS to make it boot the same mode Windows uses.  UEFI mode will require a partition for the bootloaders, but sometimes there will be a partition which looks like an EFI partition, but really isn't (since the bootloader is not bootmgfw.efi) (maybe just some vendor compatibility decision). A real EFI partition will have the boot flag in addition to being an efi partition type).

---

### Post by rccharles on 2017-01-03
quick questions:
Is there some type of log I could look in after I attempt to install Lubuntu and grub fails to install?  

Should I try to create a small partition on the disk?

Robert

---

### Post by ubfan1 on 2017-01-03
Windows 7 boots, so installing Ubuntu in the same mode does not require creating any more boot partitions of any type.  Figure out how Windows boots, and set your machine to boot the Ubuntu install media the same way.

---

### Post by oldfred on 2017-01-03
Post this, so we know if UEFI or BIOS. Windows only boots with UEFI on gpt and only with BIOS on MBR(msdos).

sudo parted -l

If UEFI system, you must use 64 bit version of Ubuntu. The 32 bit version does not support UEFI.

---

