---
title: "Installation gone Wrong.."
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by resilienceguy on 2019-12-04
Hi everyone,
I recently developed interest in Linux, my experience with it blew my mind and i decided to dump Windows for it. So i did Ubuntu installation on my laptop via USB side by side with my existing windows OS and it worked perfectly fine. At some point i decided i want to do away with the Windows OS and just have only Ubuntu running on my laptop, so did a reinstall and this time choose to erase the disk option option during installation. Now i am having issues because the installation type page goes blank; seems like the problem has to do with boot disk partition, i am a newbie and confuse.

Everything seem to have gone wrong with the installation, i will appreciate getting help to resolve this issue. I understand that i might not have provided enough information but would be glad to provide my details on request.

---

### Post by oldfred on 2019-12-04
If you have NTFS partitions with Windows hibernation flag still set that will cause issues.
Post this:
sudo parted -l

UEFI or BIOS install?
What brand/model system? What video card/chip?

---

### Post by coffeecat on 2019-12-04
Support request, not chat.

*Thread moved to **Installation & Upgrades**.*

---

### Post by resilienceguy on 2019-12-04
> **oldfred said:**
> If you have NTFS partitions with Windows hibernation flag still set that will cause issues.
Post this:
sudo parted -l

UEFI or BIOS install?
What brand/model system? What video card/chip?
UEFI Install..

---

### Post by resilienceguy on 2019-12-04
> **oldfred said:**
> If you have NTFS partitions with Windows hibernation flag still set that will cause issues.
Post this:
sudo parted -l

UEFI or BIOS install?
What brand/model system? What video card/chip?

The output you requested:
HP-Pavilion-Notebook
Model: ATA WDC WD10JPVX-60J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical) : 512/4096B
Partition Table: gpt
Disk Flags:


Number     Start        End            Size          File System          Name                    Flags
1              1049KB   538MB     537MB           Fat32               EFI System Partition  boot, esp
2               538MB    1000GB    1000GB          ext4




Model: USB Disk 2.0 (scsi)
Disk /dev/sdb: 8015MB
Sector Size (logical/physcial) : 512B/512B
Partition Table: msdos
Disk Flags:


Number    Start      End                Size           Type       File System      Flags
1            1049KB   8015MB        8014MB     Primary    fat32              boot, iba

---

### Post by oldfred on 2019-12-04
How did you make USB installer flash drive?

I have recently seen where Rufus has two modes. MBR with CSM(UEFI) which is BIOS boot. And gpt with UEFI or UEFI boot. The Ubuntu ISO is for both and most tools to create a flash drive make it so you choose as you boot, not as you make flash drive. 
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

