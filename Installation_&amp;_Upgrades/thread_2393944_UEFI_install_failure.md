---
title: "UEFI install failure"
date: 2018-06-10
forum: Installation &amp; Upgrades
---

### Post by bobsone on 2018-06-10
I am trying to load Mate 18.02 onto a separate sata HDD/SSD (sdd & sde) combo in a windows 8.1 desktop.

 As I understand the process, since this is a windows UEFI setup (fast and secure boot are off) I need to install the UEFI option on the live usb.
 
 
 Because I am installing on two new sata drives I chose the something else option and add a Boot, Root and Swap partition on the SSD and put the Home partition on the new HDD.  The issue I can not resolve is that although I can install the bios version (it works but can require 2 or 3 attempts to get it to boot) the UEFI install always fails at the grub install.

 With the UEFI install, when I get to the selection box titled **Use this device below for boot loader location**, it gives the option of **sda** which is actually the first of a two 1TB raid1 HDDs (not the windows partition).

 Because I am just experimenting with 18.04 I haven't yet tried loading the boot loader in with the windows boot partition, I have read a few comments indicating this can/may cause a problem with windows.  I have unsuccessfully tried leaving it set to **sda **and even setting the boot loader location to the **/boot (sde1)** partition on the new SSD but each time the install fails at the grub install stage.
 
 I have read a few comments stating that no matter what I do the UEFI grub install will revert to the sda partition, since sda is a storage drive, could this be what is causing my grub install failure?  

Regards.

---

### Post by ubfan1 on 2018-06-10
You're right, without an EFI partition on sda, the Ubuntu installer will fail at the grub section.  You have two choices, either add an EFI partition onto the se1 to enable booting off that device (looks like you did that), or just track down the EFI on the current booting device, and add grub to it (which really just adds an ubuntu directory under EFI, so should not affect Windows).  Manually running grub off the install media will allow either.  There are enough options on the current grub (efi version) to allow this.  The only problem I am aware of in this manual approach is the failure of the --uefi-secure-boot option to use shimx64.efi instead of grubx64.efi for the fallback/device-default bootloader .../EFI/Boot/bootx64.efi.  If you're not running secure boot, that makes no difference.  Really, under UEFI, install the bootloaders is just a matter of copying files around, no more tucking binary bits between the partitions with special tools.

---

### Post by yancek on 2018-06-10
> I need to install the UEFI option on the live usb.

I don't know how you would do that as a live usb is read only by default.  If your windows is a default UEFI/GPT install, you need to boot and install Ubuntu UEFI and to do that you need to boot the Ubuntu Live USB  UEFI.  You do not want a BIOS boot partition.  That is explained at the Ubuntu site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Creating a separate boot partition is just going to complicate things and there is really no reason to do that unless you are doing an LVM install.
The device for bootloader installation option should have a down arrow to the right and clicking that should show every drive you have connected as well as every partition on each of those drives.
The default will likely install to the already existing EFI partition used by windows on its drive and as pointed out above, create a separate directory for the Ubuntu boot files on that partition.  If you want all the Ubuntu files on separate drives, you will have to create a separate EFI partition on whichever drive you want and manually select to install boot files there.

Simplest thing to do is an EFI install with the default putting Ubuntu efi boot files on the already existing EFI partition used by windows.  If you don't want that and want them separate, you need to do this manually.  You should learn some useful things at the Ubuntu link I posted above.

---

### Post by bobsone on 2018-06-12
Thanks for the info.
Good news, I have the UEFI install working, but how do I check if the Mate 18.04 install is only on the SSD, /dev/sde... that I wanted it on? 
When I set the desktops boot order it has the SSD listed (which doesn't boot) and also has Ubuntu as a boot option (which boots reliably).  

I had a look at the drives on this desktop and (if I am reading this correctly) as expected the windows and Mate SSDs appear to have a boot sector/flag on them but it looks like the raid1 drive /dev/sda1 also has a boot sector/flag on it while the second raid1 drive /dev/sdb1 doesn't, have I missed something?

Here is the info from the two raid drives;

Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5367808f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1  *     2048 1953492991 1953490944 931,5G  7 HPFS/NTFS/exFAT




Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5367808f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953492991 1953490944 931,5G  7 HPFS/NTFS/exFAT

---

