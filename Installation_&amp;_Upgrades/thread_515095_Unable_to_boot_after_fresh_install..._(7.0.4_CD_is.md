---
title: "Unable to boot after fresh install... (7.0.4 CD iso)"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by mnslinky on 2007-08-01
I've been using FreeBSD for over 10 years, and I've decided to give Ubuntu a shot, since many of my friends use it and really enjoy it.  So, at work, I've got a desktop that's had FreeBSD since February, which I started a fresh install of Ubuntu 7.0.4 on a 160GB SATA hard disk.  The entire installation goes smoothly, up to the reboot.

Upon rebooting my system for the first time, the process stops with the following error:

[B]2.928843] ata3.00: configured for UDMA/133
2.928885] scsi3: ata_piix
3.096442] ATA: abnormal status 0x7F on port 0x0001f807
3.096544] scsi 2:0:0:0 Direct-Access       ATA     ST3160023AS    3.00 PQ: 0 ANSI: 5
3.040803] SCSI device sda: 312581808 512-byte hdwr sectors (160042MB)
3.040854] sda: Write protect is off
3.040903] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
3.041575] sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
3.045943] Uniform CD-ROM driver Revision: 3.20
3.058661]   sda1 sda2 < sda5 >
3.083804] sd 2:0:0:0: Attached scsi disk sda
3.086994] sr 0:0:0:0: Attached scsi generic sg0 type 5
3.087049] sd 2:0:0:0: Attached scsi generic sg1 type 0
Done.

             Check root= bootarg cat /proc/cmdline
             or missing modules, devices: cat /proc/modules  ls /dev
ALERT! does not exist.  Dropping to a shell!


Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu3)  built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/B]




What the heck is going on.  For the record, I've tried about 4 different flavors of linux and all of them fail to boot.  They all, however, used GRUB.  FreeBSD loads on this exact hardware just fine, every time.  Even, ahem, Windows loads OK on this hardware.

I've searched and tried most of the, 'edit your /etc/fstab file,' and menu.lst stuff, to no avail.  I'm willing to accept advice at this point, but my patience is wearing thin.

Thanks in advance for your help!

---

### Post by fredj on 2007-08-01
Go into the bios and look at any items that relate to the onchip sda controller. Usually the sda
mode can be set to either IDE, RAID (if you want to install raid) or AHCI.
WIndows XP wil happily install and boot from IDE. Ubuntu even if it installs on IDE can be
reluctant to boot from it. Feisty prefers the more advanced AHCI mode and includes the correct
drivers for it.

---

### Post by mnslinky on 2007-08-03
I checked by BIOS (Phoenix) and there isn't any options that you suggested.  I can enable/disable the SATA stuff, but that's about it.

Any other advice?  Please?

---

### Post by dabl on 2007-08-03
> **mnslinky said:**
> 

3.096442] ATA: abnormal status 0x7F on port 0x0001f807



That's not encouraging ... there's something amiss on the ATA bus, I think.  Ubuntu probably installed the bootloader on the first drive, and it's not functioning correctly.  :(

---

### Post by mnslinky on 2007-08-03
I know the drive is working correctly.  FreeBSD and Windows install and boot perfectly fine.  I don't know what that error means, but the only problems I'm having is with Linux (Debian and RedHat).

---

### Post by dabl on 2007-08-03
As an experiment, you could disable the SATA option in your BIOS. Doesn't sound like it would help, but you won't know until you try it. It sounds like there's some conflict between the hardware and the Linux drivers for your hard drive.

---

### Post by mnslinky on 2007-08-03
If I disable SATA, I can't install, since I'm using a SATA HDD.

---

### Post by dabl on 2007-08-03
Probably true -- I'm hard-headed enough that I would try it anyway, just to be sure things are as I think they are.

Are there other hard drives on that computer?

---

### Post by mnslinky on 2007-08-03
I tried, and sure enough, no hard drives found if I disable SATA.

There are no other hard drives on this system.  For note, however, I did try installing to an IDE drive earlier, but that was with the SATA stuff enabled in BIOS.  Both drives behaved the same, and the IDE drive still came up as sdx, rather than the expected hdx.

---

