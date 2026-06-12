---
title: "Ubuntu 22.04 Dualboot Windows 10 -&gt; 11"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by lukas34 on 2024-10-08
Hi,
I running my Ubuntu 22.04 in dual boot with Windows 10 which tries to confince me to update to Windows 11.
I know that before it always was a problem to upgrade/install Windows on dual boot systems after a Linux distro is installed
because Windows tends to rigorously overwrite the boot loader and only place itself in it.
Does anyone know if this is still the case now with this upgrade?
I guess no one can say for sure but maybe someone already has experience with this particular upgrade.
luggie

---

### Post by tea for one on 2024-10-08
Are both systems installed in UEFI mode (and hopefully with GPT)?
Both systems on one disk?

---

### Post by yancek on 2024-10-08
If you have an EFI system, the most likely result will be putting windows to first boot priority in the BIOS so you would have to change that to put Ubuntu first so you can boot both from Grub.  What you are describing is what happened with older Legacy boot systems where boot code was written to the MBR and overwrote what was there previously.  Running the command:  sudo parted -l will tell you if you have an EFI system as well as a GPT drive.  Windows has required EFI installs since windows 8 on a GPT drive.

---

### Post by lukas34 on 2024-10-14
> **tea for one said:**
> Are both systems installed in UEFI mode (and hopefully with GPT)?
Both systems on one disk?

Yes both are installed in UEFI mode and with GPT. Both systems are on the same drive but on different partitions. They share a common data partition (see *parted -l* below)


> **yancek said:**
> If you have an EFI system, the most likely result will be putting windows to first boot priority in the BIOS so you would have to change that to put Ubuntu first so you can boot both from Grub.  What you are describing is what happened with older Legacy boot systems where boot code was written to the MBR and overwrote what was there previously.  Running the command:  sudo parted -l will tell you if you have an EFI system as well as a GPT drive.  Windows has required EFI installs since windows 8 on a GPT drive.

yes, confirmed:

```
Model: SKHynix_HFS001TD9TNI-L2B0B (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16,8MB               Microsoft reserved partition  msftres
 3      123MB   209GB   209GB   ntfs         Basic data partition          msftdata
 4      209GB   210GB   542MB   ntfs                                       hidden, diag
 5      210GB   1024GB  814GB   ntfs                                       msftdata


Model: WDC PC SN520 SDAPMUW-256G-1101 (nvme)
Disk /dev/nvme1n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 2      1049kB  1128MB  1127MB  fat32              boot, esp
 1      1128MB  256GB   255GB   ext4
```


So you mean most likely I would simply need to change the boot order after the upgrade?

---

### Post by oldfred on 2024-10-14
Always should have good backups.

And with separate drives, you may have a setting in UEFI to disable Linux drive, so Windows will not be able to modify it. You may still have to use efibootmgr to update entry or reinstall grub as when drive disconnected, UEFI often loses UEFI boot settings for that drive.

Since two ESP, is Ubuntu using ESP on Ubuntu drive? It often default installed grub to "first" drive. UEFI/BIOS defines what drive is first drive.
Windows has defaulted to a default drive, not sure how that is defined, but some with Windows on one drive have boot from another drive.

I did have to do a total Windows recovery using Dell restore as no repairs would work. That image restore did erase my Ubuntu install and made system just like it was when purchased. Testdisk would not even see old Linux partitions. I now use Ubuntu on external SSD.

---

### Post by yancek on 2024-10-14
>   Both systems are on the same drive but on different partitions.

That is NOT what your parted output shows.  Windows is on the larger drive and Ubuntu on the smaller and you have EFI partition on both.  Look at the EFI partitions on each drive to see where the Microsoft and ubuntu directories are.  They may both be on the windows drive.  If you have an ubuntu directory on the EFI partition of the drive to which it was installed, you should be able to simply set that drive to first boot priority in the BIOS to enable booting both windows and Ubuntu.  If you upgrade to 11, you will likely need to upgrade grub from Ubuntu.

---

### Post by tea for one on 2024-10-14
As mentioned by yancek, check the location of the Ubuntu and Microsoft boot folders.
If the boot folders are stored in the respective OS disks, then you do not have to worry about upgrade to Windows 11.
Just to be sure, isolate, de-activate or physically remove the Ubuntu Disk /dev/nvme1n1: 256GB before letting Windows do its magic.

---

