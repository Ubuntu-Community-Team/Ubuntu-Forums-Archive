---
title: "Questions about dual boot install"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by R_H on 2007-01-05
Hi there everyone, linux newbie here. I apologize if there's a walkthrough that explains what to do for the following situation or if there has been a thread that already has addressed this.

I'm hoping to install Ubuntu 6.10 later today. I would like to dual boot, but I have some questions about doing so. So, without further ado, here they are.


I have 2 HDs now, a 200GB (which will be formatted and become the home for the Linux install) and a 320GB with XP currently installed on it. Can I set up a dual boot that minimizes the risk of corrupting or wiping my XP install (inadvertendly or otherwise)?

From what I understand, I need a bootloader to do this, can I choose the drive that I wanted it installed on (the MBR)? Do I have to have the XP drive connected and running, or can I install a bootloader on the unused drive, reconnect the XP drive after the install is finished and be able to select which OS to boot into?

Rig Specs
1*200GB Samsung ATA Harddrive (where Ubuntu will be installed)
1*320GB Seagate SATA Harddrive (has XP installed)
2*512MB Generic DDR RAM
Gigabyte K8T800 Pro motherboard (VIA chipsets)
AMD Athlon 64 3200+ Clawhammer S754
Sapphire 9600 Pro(?) 256MB video card

PS I imaged the C:/ partition of my Windows drive and backedup the other partitions


Thanks, any help is much appreciated :mrgreen:

---

### Post by sdowney717 on 2007-01-05
the ubuntu install will show you the drives and you can choose which one to install ubuntu onto.
You can also move a windows partition smaller to create space for a linux partition.
You will be prompted and it is fairly easy. But if you are careless, you could wipe out the windows partition in a micro second.

Ubunuts ( I like that name better) will also install the grub boot loader menu automatically.

If you want to get rid of ubunutu, use windows to delete the linux partitions.
And boot from windows install CD into recovery prompt mode and run FIXMBR to remove the grub bootloader and it will be back like it was before you played with ubunuts.

---

### Post by R_H on 2007-01-05
OK thanks. I think I understand enough to go ahead with this. Wish me luck :P

---

### Post by Bartender on 2007-01-05
Is the XP drive the primary?  Right now XP boots up, and you can see the second drive?  Are they PATA or SATA?

If they're PATA, Linux will identify them as hda and hdb.  If they're SATA, Linux will indentify them as sda and sdb.  

I'll assume you've got PATA, and you can interpret if not.  Partitions on your first drive, hda, would then go hda1, hda2, etc.

So, hda1 would have your Windows install.  hdb would be blank.  Or not.  You toss in your Ubuntu installer, make sure it recognizes both drives, then make absolutely sure you point Ubuntu at hdb, NOT hda!!

Right before the Ubuntu installer goes and does its thing, you'll get a confirmation window that summarizes the changes it's going to make.  Look for the little box that describes where GRUB is going to install.  Make sure that's "hd0".  That means Grub will install to the MBR of the Windows drive, sda.  Don't let the goofy nomenclatures throw you off, GRUB identifies partitions differently than Linux.

So just to make sure you understand, Linux installs to the second disk.  Except for part of the GRUB bootloader, which goes to the Windows MBR, giving you the option of booting either OS when you start the PC.

---

