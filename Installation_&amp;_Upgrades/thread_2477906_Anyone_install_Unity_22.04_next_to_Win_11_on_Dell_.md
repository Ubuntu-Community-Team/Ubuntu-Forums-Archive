---
title: "Anyone install Unity 22.04 next to Win 11 on Dell 7720 laptop"
date: 2022-08-10
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-08-10
Just received a refurbished Dell 7720 laptop.  It came preloaded with WIN 10 Pro, and it is currently upgrading it to Win 11.  I want to add Unity 22.04 as new laptop is replacing my 10+ year old Dell Vostro 3500 laptop.  I also plan on partitioning part of the SDD into exfat partitions for my data files so that both Ubuntu and Windows 11 apps can access the data.

Has anyone done this?  Are there any trouble spots?

Thank you,

John

---

### Post by yancek on 2022-08-11
I've never used a Dell but I can't see any specific reason it would not work.  I would expect that your windows 10/11 would be an EFI install.  Verify that before installing Ubuntu and make sure you boot Ubuntu in UEFI mode and install that way if windows is UEFI.  If you are installing Ubuntu on the same SSD, I would suggest the first thing you do is use Disk Management in windows to shrink the largest partition to make unallocated space for Ubuntu.  After doing thatt, boot windows again and run chkdsk to verify no problems.  Then boot the Ubuntu installer in UEFI mode (verify this first) and install.  The Ubuntu installer will create partitions and if you have a specific method you want, you need to use the manual install method, Something Else.

If you want a partition to share data, ntfs might be better than exfat although I believe the current Ubuntu now supports exfat.  Best to create this partition on windows before installing Ubuntu.

---

### Post by cigtoxdoc on 2022-08-12
Thank you, Yancek.  Before putting any data on the PC, I reduced the size of the NTFS partition (C:) to create two EXFAT partitions (D: and E:), an EXT4 partition (70*GB) and left the remaining space on the SSD unformatted.  Now, when I tried to install Unity 22.04, I could not direct the installation to go on the EXT4 partition.  Perhaps someone can lead me through putting Ubuntu where I want it or at least on the spare space on the SSD

Moreover, the installed failed when it said I had to unmount the CDROM.  There is absolutely no CDROM on the PC!  Is the installation program set to consider every partition labeled D: as a CDROM?

John

---

### Post by oldfred on 2022-08-13
The install media on the flash drive is then a hybrid DVD/Flash drive configuration. So installer still seen as a DVD/CDROM.

If you have partitioned in advance, you use Something Else install option and choose the ext4 partition and change to / & format (again?).
It will find & use the existing ESP - efi system partition. Only one ESP per drive. And it now creates a swap file, unless you already have a swap partition which it also automatically finds & uses. If you do not want to use the swap partition you can choose it and change to do not use. You have to have an ESP, but it only automatically uses the ESP on the first drive.

---

### Post by cigtoxdoc on 2022-08-14
Thank you, oldfred, and my apologies to the Ubuntu community for not paying attention to the Dell bootloader page.  The first time, I did not specify UEFI boot, and that made a mess of things.  When I specified UEFI boot with the Unity Ubuntu 22.04 USB stick, the installation was perfect.

PC in question is a DELL 7720 laptop.  DELL says this PC has not been qualified for Linux OS.  For not being qualified, it certainly runs Unity 22.04, so far without problems.

John

---

