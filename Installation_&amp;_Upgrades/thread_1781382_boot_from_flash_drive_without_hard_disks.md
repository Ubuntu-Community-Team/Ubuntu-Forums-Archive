---
title: "boot from flash drive without hard disks?"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by planet pluto on 2011-06-13
I have no hard drives in my computer, so I have been trying to boot Ubuntu 11.04 from an 8GB usb flash drive. Is this possible? So far the best result i have gotten is it will sit on the loading screen for a while then dump. I was only able to get the last little bit which reads
mount. mounting /dev on /root/dev failed: no such file or directory.
mounting /sys on /root/sys filed: no such file or directory.
mounting /proc on /root/proc failed: no such file or dirctory.
target file system doesn't have requested /sbin/init

---

### Post by Herman on 2011-06-13
Yes, you should be able to boot Ubuntu in a USB regardless of whether or not there are other disks plugged into the same motherboard through IDE or SATA. It depends on your motherboard's BIOS, but it seems as if yours can because it does start booting okay, it just doesn't completely boot.

The first thing I would do to try to fix it would be to take the USB flash memory installed Ubuntu to a PC running Ubuntu and run a file system check in your USB installation.
If you're not sure how to run a file system check from the command line, you can use GParted to do it, (right-click on the partition and look for 'check' in the right-click menu).

If that doesn't work you might need to re-install the USB installation's GRUB to the USB's MBR, just in case an accident has happened and it has GRUB from some other disk installed in it.

---

### Post by C.S.Cameron on 2011-06-13
Following step by step for Full install of 11.04 to USB device with no hard drives in the computer, partition sizes given are for 8GB drive:

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
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if no HDD.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.

---

### Post by planet pluto on 2011-06-16
Thank you. I have it running. Rather than just putting the installer straight on my flash drive and using the "run ubuntu from this USB" option I made an installation disc then used that to install ubuntu, using the USB as my primary (well, only) hard drive. I believe the boot error I was getting was due to something with my flash drive; I would get the same error when I tried to boot ubuntu off the disc and the flash drive was plugged in. Since formatting the flash drive for my current install I have not had that issue. My flash drive is a U3 Micro Cruzer. Which has some software in a hidden partition on it (as far as I can tell); when plugged in there is a U3 Micro Control Panel and something that shows up as a disc drive called U3 System. Not really sure what its for... but I have a feeling that its something with that that was causing the issue.

---

### Post by smurfgod on 2011-06-16
> **C.S.Cameron said:**
> Following step by step for Full install of 11.04 to USB device with no hard drives in the computer, partition sizes given are for 8GB drive:

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
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if no HDD.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.

I'm gonna be using this method to install onto a 16 gig usb drive. Thanks man

---

