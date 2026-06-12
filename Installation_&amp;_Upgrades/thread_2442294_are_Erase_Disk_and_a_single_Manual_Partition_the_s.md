---
title: "are Erase Disk and a single Manual Partition the same thing?"
date: 2020-05-02
forum: Installation &amp; Upgrades
---

### Post by anotherChris on 2020-05-02
When using the installer, is the Erase Disk option the same as choosing Manual Partitioning option and then making only a single **ext4** partition that uses the entire disk space?

If the answer is no...

Then, if I did the latter, would the installer automatically manage boot files, or would making only a single **ext4** in Manual Partition make something break?

If the answer is yes...

Then, why would the installer ever force you choose Manual Partitioning (it did to me when installing Lubuntu 20.04 on a 8GB stick computer by not showing the Erase Disk option)?

---

### Post by Impavidus on 2020-05-02
The erase disk option will wipe the entire disk and create one big ext4 partition. If you use UEFI mode (and if you're on a new computer and not dual booting with an already installed OS [and, given that you wipe the disk, you aren't], you should), it will also create an EFI partition. In the past it also created a swap partition, but this has been replaced with a swap file.

If you've got multiple hard drives, the erase disk option doesn't make it clear which disk to erase. With multiple hard drives (including usb drives), it's best to use manual partitioning.

If you use manual partitioning, the installer will do exactly as you tell it and will give an error if this is invalid.

---

### Post by CelticWarrior on 2020-05-02
And if using manual partitioning you need to create the EFI partition, not a single EXT4 partition occupying the whole disk. Installation will fail because of that.

---

### Post by Dennis N on 2020-05-02
> When using the installer, is the Erase Disk option the same as choosing Manual Partitioning option and then making only a single ext4 partition that uses the entire disk space?

This used to be true, but not with the Ubiquity installer in Ubuntu 20.04.

Erase Disk and install creates a MS-DOS partitioned disk (in BIOS mode). Based on the evidence shown below, If you install in BIOS mode, the resulting partitions from this choice have changed in 20.04 from 19.10. Compare Ubuntu 19.10 and recently installed Ubuntu 20.04 (both are VM installs here - but I don't see that making any difference in what the installer does):

**Ubuntu 19.10** - how it used to work:
```

Disklabel type: dos
Disk identifier: 0xb3867453

Device     Boot Start      End  Sectors Size Id Type
/dev/vda1  *     2048 50329343 50327296  24G 83 Linux

```
**Ubuntu 20.04** - how it works now:
```

Disklabel type: dos
Disk identifier: 0x5a8580ee

Device     Boot   Start      End  Sectors  Size Id Type
/dev/vda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/vda2       1052670 41940991 40888322 19.5G  5 Extended
/dev/vda5       1052672 41940991 40888320 19.5G 83 Linux

```
The installer default in 20.04 BIOS install created an EFI system partition and an extended/logical structure for the OS. The EFI partition is empty, but still mounted at /boot/efi. 

So based on this evidence, if you want a single partition BIOS system, I suggest you manually partition.

---

### Post by anotherChris on 2020-05-03
> **Dennis N said:**
> This used to be true, but not with the Ubiquity installer in Ubuntu 20.04

I'm using Lubuntu 20.04.  When I do sudo fdisk -l and sudo parted -l, I get the following:


```
Disklabel type: dos
Disk identifier: 0x6e219bc0

Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1        2048 312576704 312574657  149G 83 Linux
```

```
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  160GB  160GB  primary  ext4
```

So, Lubuntu and Ubuntu are using versions of installer?

---

### Post by Dennis N on 2020-05-03
> So, Lubuntu and Ubuntu are using versions of installer? 
As far as I know, Lubuntu is still using the Calamares Installer. Lubuntu switched to that from Ubiquity (used by Ubuntu) starting with Lubuntu 18.10. The comments in Post #4 were about the Ubuntu installer (as it says in the post), not Lubuntu's, just to point out the difference in how it now does the partitioning - 19.10 compared to 20.04. Sorry for the confusion.

---

