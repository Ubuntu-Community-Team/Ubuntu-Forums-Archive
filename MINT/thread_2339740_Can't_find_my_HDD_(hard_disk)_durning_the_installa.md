---
title: "Can't find my HDD (hard disk) durning the installation of the Operative System"
date: 2016-10-12
forum: MINT
---

### Post by marcop2 on 2016-10-12
Hey All, Im literally going crazy...
Im trying to install Ubuntu (and then Mint) on my desktop pc, as unique operative system, easy right? Nope!
When the boot of the os start (im installing via usb) everything goes ok until i have to chose where i want to install Ubuntu.
The o.s. try to install his-self inside the usb key without allow me to select where.
I've follow some guides finded here, and i have discovered that ubuntu _*did not recognize my hdd*_.

I try to use Gparted, and this is the output:

[IMG]https://s9.postimg.org/syjocsldb/14699529_276776436055245_977093506_o.jpg[/IMG]

**my pc mount**:  

**CPU**: AMD Athlon(tm) x4 750k Quad Core Processor
**Graphic Video**: GeForce GTX 650
**HDD**: ST2000DM 001-1CH164 SATA Disk Device

**Priority device boot selected** in the bios is sata.
**secure boot**: [Disabled]
**Fast Boot**: [Disabled]

Hope you can help me! And thank you!

---

### Post by oldfred on 2016-10-12
post these:
sudo fdisk -lu
sudo gdisk -l /dev/sda

If HDD is not sda, change to correct drive.

Does BIOS/UEFI see drive correctly. Some have settings to lock or prevent seeing drive.
Is drive set for AHCI, not old IDE nor RAID?
Was drive ever in RAID mode, or Intel SRT which looks like RAID?

---

### Post by leunam12 on 2016-10-12
Does BIOS see the drive?

---

### Post by howefield on 2016-10-12
Thread moved to the "*MINT*" sub forum.

---

