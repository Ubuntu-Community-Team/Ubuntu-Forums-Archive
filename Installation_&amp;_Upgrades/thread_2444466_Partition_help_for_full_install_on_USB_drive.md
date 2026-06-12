---
title: "Partition help for full install on USB drive"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by ndc320linux on 2020-05-30
Hello everyone

I am trying to install Ubuntu 20.04 for a friend on a 64GB Samsung USB pen drive. I have been reading some guides on how to do this but I have some questions I would appreciate anyone's help with to resolve - all help and support is really appreciated. 

The intention was to use circa 60GB for the main "/" partition, and a 4GB "swap" partition - no separate home partition required. However from the guides I have been reading - I believe I need a FAT32 partition with the name of the drive. I am quite confused by this as my experience is limited to just installing recently Ubuntu on a desktop machine to dual boot Windows 10. Why do I need a FAT32 partition with the name of the drive? And what size should this be - is there a recommended size for a 64GB drive? 

Plus, also something I am not sure about is about the "biosgrub" partition? I am not sure why this is required as the boot loader needs to go onto the USB drive. 

For reference, this install won't touch the UEFI install of Windows 10 professional. Fast boot/secure boot is assumed to be enabled on the machine but as the install won't touch Windows 10 I thought this wouldn't matter - I hope this isn't completely wrong.  

The drive will be completely formatted as "unallocated space" ready for the install. This will be done on Windows with the partition manager to get the drive ready for the install. 

Thanks again for any help and support - please also accept my apologies for such a basic Linux knowledge... I am indeed still learning and growing here.

---

### Post by yancek on 2020-05-30
The bios_grub partition is only needed if you are installing in Legacy mode on a GPT drive.  If you are doing an EFI install, you do not need the bios_grub partition but you do need an EFI partition on the USB rather than the internal hard drive with windows which will be the default during the install.  An explanation of bios_grub and EFI is given at the Ubuntu documentation site below as well as other pertinent information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kurt18947 on 2020-05-30
I'm barely literate about this stuff but I'm pretty sure you want a small (100MB?) FAT32 partition on any drive you plan to install as UEFI. I generally make that FAT partition first then ext4 or whatever file system you prefer. You want to minimize writes on flash media but steps to accomplish this are beyond my skill level. Ubuntu defaults to a swap file so no swap partition needed. If you're using a machine on which the hard drive is readily accessible, you might consider disconnecting/removing it after creating your live USB but before installing the full OS. You want to make sure the O.S. and bootloader are installed in the intended places. It's not that difficult to install in the wrong place and overwrite your existing installation. Been there got the T-shirt.

---

### Post by oldfred on 2020-05-30
You need the ESP - efi system partition & / (root).
Ubuntu's default now is to use a swap file, so no swap partition required.

But Ubuntu's ubiquity installer will install grub to ESP on internal drive, no matter what selections you make during install. Those options only work with BIOS installs.
See this for a work around. In middle of install you unmount internal drive's ESP and mount ESP on flash drive. You also have to edit fstab afterwards, as it still uses the internal drive's ESP.
Posted work around to manually unmount & mount correct ESP during install posts #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Similar post:
[https://ubuntuforums.org/showthread.php?t=2444453](https://ubuntuforums.org/showthread.php?t=2444453)

You do want to change some settings to reduce writes like a SSD. But many settings for SSD will not work with flash drive.
I just upgraded my M.2 SSD to NVMe and put SSD into external case. Very fast. For larger flash drives I may now use SSD, but more expensive. I do also remember first flash drive was both small and expensive.

With gpt, you need either ESP or bios_grub. I have both just in case I want to convert from UEFI to BIOS boot. One of my flash drives:
```
Model:  USB DISK 3.0 (scsi)
Disk /dev/sdb: 248GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  530MB   528MB   fat32        esp256    boot, esp
 2      530MB   531MB   1049kB                         bios_grub
 3      531MB   26.7GB  26.2GB  ext4         focal256
 4      26.7GB  248GB   221GB   ext4         data256a

```

My "new" USB M.2 drive that used to be my main working SSD on this system. Now an external drive.
```
Model: Samsung SSD 850 EVO (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  53.5GB  53.5GB  fat32        ESP      boot, esp
 2      53.5GB  86.0GB  32.5GB  ext4         xenial
 4      86.0GB  113GB   27.3GB  ext4         bionic
 5      113GB   210GB   97.1GB  ext4         m2_data
 3      228GB   250GB   22.0GB  ext4         ISO

```

---

### Post by C.S.Cameron on 2020-05-31
Here is a step by step guide for making a Full install USB drive that boots in BIOS or UEFI mode:
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)
The /home partition is optional.
You do not need a swap partition as Ubuntu now creates a swap file.
If the computer you create the USB on has a swap partition, you might want to create a swap file by hand and remove the existing swap partition from fstab.
A Data partition is a good idea so you can still use the drive for Data on Windows and Linux computers.
If you use Apple computers you might prefer a FAT32 rather than NTFS Data partition.
If you create the device booted in UEFI mode with existing HDD plugged in, remove EFI line from fstab.
PM me if you need any help with it.

---

