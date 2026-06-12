---
title: "Booting installation from hard drive using usb flash drive?"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by splintered on 2012-01-12
Hi,

I'm new to Linux in general and have been using Ubuntu for awhile, but am looking to try and set up functionality that I'm having trouble with. I have a system set up to dual boot Windows 7 and Ubuntu; the Windows 7 partition is encrypted with TrueCrypt, so I am using that boot loader currently, which does not give me the option of loading the Ubuntu installation.

What I would like to do is to install GRUB onto a flash drive, which I could then use to either boot Ubuntu or allow me options for booting the TrueCrypt partition. Without that flash drive connected, I would like the TrueCrypt bootloader to load as it does now. If possible, I would also like to find a way to install an Ubuntu Live USB installation on the same flash drive, so I would have the option of running the Live installation, loading the installation on my internal hard drive, or booting the TrueCrypt bootloader.

The biggest problem I'm having is getting GRUB to install on the flash drive. I've come across a few tutorials online for this type of thing, but they all seem to be taylored to slightly different situations, and none are working properly for me. Specifically, I am not sure about how to partition and format the flash drive (a) to use GRUB in the way I am looking to use it, and (b) to allow it to also have the live install. Finally, I am having trouble figuring out what changes I need to make to get it to properly load the installations off of my internal hard drive even though I'm booting off the flash drive.

Any help or direction is greatly appreciated. I've seen a few tutorials on this forum and online, but again, haven't been able to find a solution. Thanks in advance,

Mathew

---

### Post by C.S.Cameron on 2012-01-12
Following step by step for Full install of 11.10 to USB device.
You should get the grub option to boot the thumb drive or the other O/S on your system.
Partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

