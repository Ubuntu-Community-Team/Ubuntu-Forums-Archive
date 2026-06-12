---
title: "Ubuntu doesn't boot after installing in UEFI mode."
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by weekend_player on 2012-11-12
Hello, I Installed Ubuntu 12.10 64bit in UEFI mode and after restarting laptop i get "Failed to verify image with *ACCESS DENIED" instead of grub and then it boots Windows 8. I tried boot-repair but didn't help. Any Ideas?

---

### Post by oldfred on 2012-11-12
Must be related to secure boot.

Post link to BootInfo report.

'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Some have turned off secure boot to get it to work, but better to review that it is installed correctly first.

---

### Post by weekend_player on 2012-11-12
[http://paste.ubuntu.com/1353377/](http://paste.ubuntu.com/1353377/)

---

### Post by oldfred on 2012-11-12
It looks like you installed in BIOS mode as you have a bios_grub partition and grub installed to MBR.

If Windows is in UEFI mode you have to have Ubuntu in UEFI mode. Use Boot-Repair and make it convert to UEFI mode.

You have this error in your sdb protective MBR. gpt drives use a gpt partition table but create one large partition in a protective MBR so older partition tools do not think it is not formated.
> 
/dev/sdb1 ends after the last sector of /dev/sdb

Try using gdisk, you can download from repository into liveCD and see if just loading it fixes it or not.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by weekend_player on 2012-11-12
I think I installed it in UEFI mode, but when it didn't boot I run Boot-Repair -> "Recommended repair" and it asked me to create that bios_grub partition... /dev/sdb is SSD drive so I wouldn't touch it... When I run boot-repair this time it didn't have the option to convert it to UEFI, so I read in the tutorial that:

> Since Ubuntu 12.04, it is possible to re-use an existing Windows7  EFI partition (without formatting it). If you use a previous version of  Ubuntu, or if you have several installations of GNU/Linux in EFI mode,  it is safer to create a new EFI partition EFI.

An EFI partition can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is ok), and must have the following attributes: [I]
- Mount point:[/I]  /boot/efi  (remark: no need to set this mount point when using the  manual partitioning, the Ubuntu installer will detect it automatically)[I]
- Size:[/I] between 100MB and 250MB[I]
- Type:[/I] FAT32[I]
- Other:[/I] must be located at the start of a GPT disk, and must have a "boot" flag. I don't want to mess up windows 8 because I need my laptop for university. There is a partition that looks like it's efi partition (300 MB, fat32, boot flag), it's /dev/sda2 but it is bigger than 250MB. Can I just shrink it to 250? Will Boot-Repair detect it?

---

### Post by oldfred on 2012-11-12
BootInfo shows sda2 as your efi partition. In gparted it is the boot flag on a FAT32 partition. But in gpt partitioning the internal code is ef00 which means it is the efi partition.

Did you boot the Ubuntu or Repair CD or flash drives from UEFI in UEFI mode not BIOS/AHCI or whatever. How you boot liveCD is how it installs or repairs. So you want to boot in UEFI mode.

The UEFI spec says it should be first, but Windows says the Vendor recovery can be first and efi second. We have seen one or two with it as the third partition. I think, but do not really know that the FAT32 driver in the UEFI code just cannot read large drives so they want it near the front of the drive. Saying it must be first simplifies the explanation.

---

### Post by weekend_player on 2012-11-13
I always boot in UEFI mode, because if I don't, windows 8 won't boot. I've installed ubuntu that way and it didn't work. 

I've read your post but still don't know** if I can resize that efi partition to 250mb and will boot-repair recognize it then?** (and is it safe to do so...)

---

### Post by oldfred on 2012-11-13
You can resize it, but I have seen recommendations all over the place, yous does not look too large. But you are using only 15%, so you can shrink. 

I think many of the recommendations are to make it plenty large as the first partition or early partitions would be difficult to make larger later and are not sure if future needs may need more space.

---

