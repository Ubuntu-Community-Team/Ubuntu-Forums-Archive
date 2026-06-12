---
title: "Major boot problem, failed upgrade to 15.10, UEFI and single-boot"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by anje on 2015-10-30
Hi all, 

Tried to upgrade Xubuntu 15.04 to 15.10 yesterday on my Asus N550JK laptop, and I've been having boot problems ever since. First I was only getting a grub prompt, and trying to define where to locate vmlinuz and initrd revealed that I didn't have an initrd corresponding to the most recent kernel. Several attempts to install Xubuntu, Linux Mint, and Ubuntu over each other as clean installs has apparently further trashed my boot sector.  (Edit: I had previously wiped most of Windows off the computer except for the 100MB EFI. Trying to do complete fresh installs when the first one failed clearly killed that. I don't need Windows back, especially Windows 8 in any case, so solutions don't have to maintain a dual boot.)

I have tried running boot-repair in the current live version of Linux Mint. It first suggested that I needed an unformatted partition with the boot_grub flag, which I created with gparted (I made it 500MB). Now it's saying "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a [sic] EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag). Do you want to continue?"  Gparted seems to indicate that I already have this partion present. 

I let boot-repair run overnight, but the part where it's supposed to be reinstalling "last kernel sda2(ins)" is apparently hanging and spinning, because I haven't gotten any forward progress beyond that step in two attempts.

Boot-repair gives me this URL to share: [http://paste2.org/nvF0K25C](http://paste2.org/nvF0K25C)

Help me Obi-Wan! I need my computer back!


tl;dr -- Grub won't install.


Edit:  In the end, what made it work was installing from a DVD instead of a USB flash drive. Glad my computer has an optical drive.

---

### Post by oldfred on 2015-10-30
With gpt partitioning Windows only boots in UEFI boot mode.
But with gpt Ubuntu can boot in either UEFI or BIOS boot mode, if correct partitions are on drive.
And how you boot installer UEFI or BIOS is then how it installs. You should have two boot options in UEFI to boot installer flash drive. One usually is clearly UEFI:flashdrive and other just is flash drive's name.

With BIOS Boot & install you have to have the bios_grub partition. It must be unformatted and only needs to be 1 or 2MB. You set bios_grub flag using gparted or ef02 code with gdisk.

With UEFI boot and install you need a ESP - efi system partition. It is FAT32 formatted and has boot flag is using gparted or ef00 if using gdisk. Windows defaults to 100MB, but most suggest 300 to 500MB if you have larger hard drive and space not critical. In future you may want more space for other UEFI options. If flash drive then smaller ok.

With any Linux install and correct partitions you can use Boot-Repair to totally uninstall/reinstall grub2. It can then also convert from/to UEFI or BIOS by reinstalling correct grub. Grub is grub-efi-amd64 for UEFI boot and grub-pc for BIOS boot. But you need to boot installer in correct mode you want and then install Boot-Repair.

So for UEFI boot, boot installer in UEFI mode from UEFI boot menu. Add Boot-Repair. In advanced options choose the full uninstall/reinstall options.

Also shows boot screens, so you know you which way you have booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anje on 2015-10-30
I'm away from the box at the moment, so bear with me. Hooray tablets? 

Thumb drive only had UEFI boot  option in the 64bit flavor, which is what I installed with. As you can see from the boot-repair output, a designated FAT32 EFI partition with boot  flags should be present. That was there when I started trying to alter the partitions.  I'll  double check that, though. However, boot-repair isn't completing in any case. I'll have another run-through with it when I get home.

Repeated attempts to install the UEFI, including wiping the hard drive and having the installer repartition it by default have all failed. It has failed using both a Linux Mint 17.2 installer and with the latest Ubuntu 14.04.3 LTS installer. I get messages like: > The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.
Then it tells me that the installer has crashed and falsely promises that when I close the window (which won't close), I will be taken to file a bug report.

Similarly, as stated before, boot-repair fails to complete installing the kernels. It just hangs. 

What can I do? Is this software or hardware?

---

### Post by oldfred on 2015-10-31
Post this from Live installer:
sudo parted -l

---

### Post by anje on 2015-10-31
Here's what I got: 
```

mint@mint ~ $ sudo parted -l
Model: ATA SanDisk SD6SB1M2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  538MB  537MB   fat32                 boot
 2      538MB   239GB  238GB   ext4
 3      239GB   256GB  17.1GB  linux-swap(v1)


Model: IT1165 USB Flash Disk (scsi)
Disk /dev/sdb: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.2GB  16.2GB  primary  fat32        boot, lba

```

While I'm at it, here's fdisk's output: 
```

mint@mint ~ $ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37605fdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   500118191   250059095+  ee  GPT

Disk /dev/sdb: 16.2 GB, 16236150784 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31711232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31711231    15855584+   c  W95 FAT32 (LBA)

```

Edit again. This is what I get for boot options. 
[img]http://i.imgur.com/YM1OUhe.jpg[/img]

---

### Post by oldfred on 2015-10-31
Fdisk does not work with gpt drives. I think it was finally updated with 15.10. Normally parted or gdisk.

Partitions look ok.

Perhaps more details. Did you do anything special before to make it boot in UEFI boot mode?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by anje on 2015-10-31
[RIGHT]&#8593;
You can kinda tell I don't 
come here to ask for help
very often. [/RIGHT]

I was using gparted for the actual partition editing, not fdisk. Just looking for what outputs have been asked for in similar situations. :/ Didn't do anything special before to make it boot into UEFI. Based on some of the other troubleshooting messages, I should mention that I have been connected to the internet for all installation attempts.

Boot repair summary: [http://paste2.org/k26ZYhJE](http://paste2.org/k26ZYhJE)  You'll note that I made another attempt to install Ubuntu 14.04.3. Default options, told it to erase the disk. (My usual operation is to install editing the partition table manually, as I prefer to have a separate /home partition, but right now my priority is to get the computer to boot at all.)

---

### Post by ubfan1 on 2015-10-31
I see no bootloaders at all on sda -- they should be in the EFI partition under /EFI/ubuntu/... for a UEFI install.  I assume we are not interested in a legacy install, using the MBR for the bootloader, but it's not present either. The EFI partition exists, has a FAT filesystem, and is flagged bootable, all good.  Not sure why the grubx64.efi and shimx64.efi did not get copied into the normal location.  Maybe from the live media, run  
sudo grub-install /dev/sda
but first ensure you are in UEFI mode.

---

### Post by anje on 2015-10-31
From the live media, sudo grub-install /dev/sda returns: 
```
grub-probe: error: failed to get canonical path of `/cow'.
Installing for i386-pc platform.
grub-install.real: error: failed to get canonical path of `/cow'.
```

 For some reason I've consistently failed to get it to install the bootloader, using several different distros now (Xubuntu 15.10, Xubuntu 14.04.3, Mint 17.2) and a couple different flash drives. It makes me wonder if there's a deeper problem with the debian installer as it relates to my system, or whether there's something fishy happening with my SSD, now that the warranty's up.

---

### Post by oldfred on 2015-11-01
Sometimes the FAT32 partition gets corrupted. And then installers & script cannot correctly see it.

I might try fsck on the FAT32 partition sda1.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by anje on 2015-11-01
> **oldfred said:**
> I might try fsck on the FAT32 partition sda1.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1


Interesting. That returns the following: 

fsck.fat 3.0.26 (2014-03-07)
There are differences between boot sector and its backup. 
This is mostly harmless. Differences: (offset:original/backup)
  65:00/01
  Not automatically fixing this.
/dev/sda1: 1 files, 1/130812 clusters

---

### Post by oldfred on 2015-11-01
Boot sector normally has a backup and if you change boot sector incorrectly then you can restore the previous one.

Do not think that would create issues with installing grub to FAT32 with boot flag or ESP - efi system partition.
But if reinstalling I might delete & recreate that partition also. I assume that is the only thing you did not change before when reinstalling and issue persisted.

---

### Post by ubfan1 on 2015-11-01
I think your grub install was the legacy grub, not the grub-efi-amd package for UEFI.  The legacy rub does not write anything to the EFI FAT anyway.

---

### Post by anje on 2015-11-01
I have tried deleting and remaking the boot partition, approximately 5 times now. Reformatting it too.

I didn't intentionally install legacy grub. Is that what Ubuntu is defaulting to now when you tell it to erase everything, make new partitions, and install fresh?

---

### Post by oldfred on 2015-11-01
Probably better to install with UEFI, but if installing in BIOS boot mode, you need a 1 or 2MB unformatted partition with the bios_grub flag.
I typically put both the ESP & bios_grub on all drives, but once I have the UEFI system I only use UEFI booting. The bios_grub is for my old system that only boots in BIOS mode. 

How you boot installer is then how it installs. UEFI should give two options to boot, one UEFI and one just name of flash drive or BIOS.
Once you boot you can tell which way you have booted, if not sure:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anje on 2015-11-01
I'm installing with UEFI.  The only reason I messed with the bios_grub flag at all is because boot-repair insisted that I needed it. Anyway, as you can see from my partition table, that's gone now.

---

### Post by anje on 2015-11-01
Picked a brain locally, and got the suggestion to try installing from a DVD instead of USB. There's no reason why this should work better that I'm aware of, but it did. I did everything else identically to the last time, down to the password.

So... if you all can figure that one out, good luck!

---

