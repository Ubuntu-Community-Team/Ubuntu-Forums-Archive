---
title: "GRUB not showing up when dual booting"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by Isaac_Moselle on 2014-08-23
Hello,
I have recently installed ubuntu on a laptop which came pre-installed with windows 8.1. However, after the install I was prompted to restart and windows loaded up as normal (there is no GRUB). I have disabled fast-boot and enabled CMS, and used boot-repair in a live-session which didn't fix the problem. Here is the summary: [http://paste.ubuntu.com/8122139/](http://paste.ubuntu.com/8122139/). My computer is an Asus ROG G750JM-DS71, and the OS is windows 8.1 64-bit. I have never used linux before, so there is a chance i'm missing something really obvious.
Thanks

---

### Post by fantab on 2014-08-23
You should NOT enable CMS, which is nothing but the older BIOS mode or 'legacy' mode. Windows8.1 most likely installed in UEFI mode which is default now.
You cannot have one os in UEFI and another in CMS.

Disable CMS or enable UEFI and reinstall Ubuntu. How you boot your install media is how it will install; meaning, if you boot Ubuntu DVD/USB in Uefi mode then it will install in Uefi mode.
[See Here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").

Also:
```

parted -l:

Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  106MB   105MB   fat32           EFI system partition          boot
2      106MB   1050MB  944MB   ntfs            Basic data partition          hidden, diag
3      1050MB  1184MB  134MB                   Microsoft reserved partition  msftres
4      1184MB  255GB   254GB   ntfs            Basic data partition          msftdata
**6      255GB   255GB   1049kB                                                bios_grub**
7      255GB   966GB   711GB   ext4
8      966GB   979GB   12.8GB  linux-swap(v1)
5      979GB   1000GB  21.5GB  ntfs            Basic data partition          hidden, diag
```

Your 6th partiion or /dev/sda6 is only needed if you boot a Linux OS in CSM from GPT disk.
Either delete this partition before you re-install or just remove the 'bios_grub' flag from the partition using Gparted.

good luck...

---

### Post by Isaac_Moselle on 2014-08-23
Thank you for replying! I will try this solution.

---

### Post by Isaac_Moselle on 2014-08-23
Hmm... Now the disk drive doesn't show up in the boot menu. Only the hard drive.

---

### Post by oldfred on 2014-08-23
Post a new link to BootInfo report from Boot-Repair.

---

