---
title: "USB ubuntu problem!!"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by Shankal on 2012-01-01
I decided to install ubuntu on a 8gig usb flash using the installation wizard of ubuntu on windows 7, picking the flash as the installation directory.
the installation went clean and all, and ubuntu is working fine but i keep getting the "The volume "Filesystem root" has only xMB disk space" message.
is there any way to reinstall it properly or resizing.
i am using ubuntu 11.10

---

### Post by coffeecat on 2012-01-01
Question 1: is the "installation wizard of ubuntu on windows 7" that you refer to, the wubi.exe wubi installer?

Question 2: is the 8GB flash drive formatted with a FAT filesystem?

If yes to both, that means that your root.disk virtual Ubuntu partition is only 4GB, which is not large enough. FAT filesystems do not permit file sizes greater than 4GB, so you will not be able to create an Ubuntu virtual partition greater than 4GB unless you reformat the drive. (The wubi Ubuntu virtual partition is contained in a single file called root.disk.)

You would need to reformat the flash drive to NTFS, which would allow a larger virtual partition, or install your wubi installation elsewhere. Formatting a flash drive with a journalled filesystem such as NTFS may reduce its life, though.

If the answer to either of my questions is no, then please give us more information.

---

### Post by C.S.Cameron on 2012-01-01
Following step by step for Full install of 11.10 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

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

### Post by Shankal on 2012-01-01
> **coffeecat said:**
> Question 1: is the "installation wizard of ubuntu on windows 7" that you refer to, the wubi.exe wubi installer?

Question 2: is the 8GB flash drive formatted with a FAT filesystem?

If yes to both, that means that your root.disk virtual Ubuntu partition is only 4GB, which is not large enough. FAT filesystems do not permit file sizes greater than 4GB, so you will not be able to create an Ubuntu virtual partition greater than 4GB unless you reformat the drive. (The wubi Ubuntu virtual partition is contained in a single file called root.disk.)

You would need to reformat the flash drive to NTFS, which would allow a larger virtual partition, or install your wubi installation elsewhere. Formatting a flash drive with a journalled filesystem such as NTFS may reduce its life, though.

If the answer to either of my questions is no, then please give us more information.


Thank you for the quick reply.

yes is the answer for both of your questions...i formatted the flash stick using fat32 filesystem
and i used the wubi installer.

can i get more details on installing the wubi installation elsewhere.

FYI i used Daemon tools to mount the iso image for the installation.

---

### Post by coffeecat on 2012-01-01
@Shankal, if you are wanting to create a wubi install, it is far better to install it to your hard drive. Most people use the Windows C: partition. If you have plenty of spare space on your C: drive, then you can make the wubi installation large enough for your needs.

Here are a couple of guides for you:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Before you do a fresh installation of wubi, uninstall your current flash drive one from within Windows - make sure the flash drive is plugged in when you do this. If you don't do this you will end up with two Ubuntu entries in your Windows BCD boot menu, one of which won't work.

---

