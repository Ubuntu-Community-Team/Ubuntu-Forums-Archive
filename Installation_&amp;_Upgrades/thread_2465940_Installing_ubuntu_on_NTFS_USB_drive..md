---
title: "Installing ubuntu on NTFS USB drive."
date: 2021-08-16
forum: Installation &amp; Upgrades
---

### Post by tomshellybaster on 2021-08-16
How do you install ubuntu on NTFS for a thumb drive?  I've been looking at Rufus and I'd rather not have to format and etc. my thumb drive all remaining options to figure out how it works.  I've read the online documentation and I don't like FAT or FAT32 since they're out of date, and I want to have my Ubuntu with NTFS for dual compatibility for the 1 TB thumb drive. 

I tried FreeDOS and my laptop won't boot with Ubuntu, but once I managed to get it to work, but not with NTFS.  I have a American Megatrends laptop Ryzen 5 with Radeon integrated graphics.

---

### Post by sudodus on 2021-08-16
You cannot install Ubuntu into the NTFS file system. Ubuntu is a Linux distro and uses Linux file systems. It can read and write data from NTFS and other Windows file systems, but it needs a Linux file system for the root partition. The standard file system is ext4.

If you don't want to touch the partition table and file system of your thumb drive, I suggest that you get a new one and dedicate it to Ubuntu.

You can start from [this link](https://ubuntu.com/download/desktop) and links from it. There are links for downloading an Ubuntu Desktop iso file, and links to instructions how to make a bootable USB drive with Ubuntu.

---

### Post by tomshellybaster on 2021-08-16
My computer does not have a BIOS, but a UEFI. Is there any recent developments on the NTFS being other than read-only under UEFI (mentioned in one documentation)?

---

### Post by sudodus on 2021-08-16
NTFS is the main file system used by Windows.In recent years Windows is installed in UEFI mode (when delivered with the computer, 'factory installed'). And it is read/write (not read-only).

---

### Post by yancek on 2021-08-16
Your initial post is a little confusing (to me at least).  You mention installing Ubuntu to an ntfs drive which won't work as explained above but you also mention Rufus which is used to create a bootable usb.  Which is it?  You can put an Ubuntu iso file on an ntfs (or any other filesystem formatted) partition on a flash drive or hard drive and boot it but you will need Grub2 installed on the hard drive (or flash drive) to boot it.  If you are trying to boot Ubuntu installer from a USB, you will need to check the Rufus or other site to see if this is permitted.  Some of this software does require FAT32 format to work.

---

### Post by oldfred on 2021-08-16
If you want to boot in UEFI boot mode, you must have boot files in an ESP - efi system partition which must be FAT32 with esp, boot flags.
Installer is configured as FAT32. FAT32 is ok for smaller partitions and where you do not need large files over 4GB.

---

### Post by C.S.Cameron on 2021-08-17
You can install Ubuntu Persistent Live to a NTFS USB drive using Rufus, YUMI or Universal USB Installer.

This would not be a Full install as you would do to an internal drive and has limitations such as speed. See: [https://askubuntu.com/a/1341121/43926](https://askubuntu.com/a/1341121/43926)
Rufus puts it's persistence on an ext4 partition. UUI and YUMI put everything on a single NTFS partition.
At least a Persistent install to NTFS would give you the opportunity to explore Ubuntu.

One major problem is that NTFS partitions are easily fragmented and fragmented drives do not boot. It is very hard to actually fully defragment a drive.   

If you want something fancy, Ventoy uses an exFAT filesystem and not old fashion FAT32 or NTFS.
Ventoy requires a free add on for unlimited persistence.
Ubuntu still needs an add on to read/write to exFAT.

---

