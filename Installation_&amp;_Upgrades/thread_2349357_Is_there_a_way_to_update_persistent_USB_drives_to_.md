---
title: "Is there a way to update persistent USB drives to boot under UEFI?"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2017-01-13
I had a previous laptop that didn't use UEFI. I made a bunch of USB persistent sticks that I use for a bunch of different reasons. Old laptop crapped out. Got a new one. New one is dual boot with Win 10 and Ubuntu 16.04. It's set up with UEFI. Now, none of my old persistent USB sticks are recognized even if I press F12 and go into boot mode. I haven't done a detailed comparison but it looks like on new USBs, I get a UEFI folder and when I boot, I get another option that shows up if I go into boot mode (F12).

All these persistent drives a highly configured and I don't want to start over. Is there a way to make them work in a UEFI environment? Dual booting Win and Ubuntu works fine

Acer Aspire F 15 F5-573G-56CG

---

### Post by oldfred on 2017-01-14
The Ubuntu live installer boots in either UEFI or BIOS boot mode.
So is issue that your Acer is not allowing USB boot?
Or are the  USB flash drives very old versions of Ubuntu?

I find if I want to customize a larger flash drive with new systems and USB3, it is better just to do a full install. I have full installs in several 32 & 64GB flash drives.
But UEFI full install to flash drive is a bit more difficult. You have to partition in advance, make sure you have the ESP - efi system partition and backup your ESP on sda. Grub only installs to ESP on sda. You then have to copy /EFI/ubuntu to ESP on flash drive twice, once to /EFI/ubuntu and once to /EFI/Boot and rename shimx64.efi to bootx64.efi.
That is becuase grub only installs to sda in UEFI mode. And UEFI only boots /EFI/Boot/bootx64.efi on external drives.

Do you have /EFI/Boot/bootx64.efi on your persistent drive? That version of grub/shim is different than the full install version but should be there.

---

### Post by PopsTheSailor on 2017-01-14
Sorry here are a few more details.

On the new computer I was able to create a USB drive the boots if I go into the boot menu (F12) and manually select it. I'm sure I get it to automatically boot and that's not my issue. But I previous made bootable USBs on a non UEFI laptop. Any of those I put into a USB port and then go into F12 don't show up at at all. I did a quick look and on the old ones, I didn't see an EFI folder where I have one on the USB that works. I agree, I'm going to buy some larger USBs and just do a full install but again that's not really my problem right now. 

My problem I'm trying to fix right now is how to get my old USBs to boot on the new laptop with UEFI. I've invested quite a bit of effort into their configuration and would hate to start over, but I will if I have to. Could I simply copy a /EFI/Boot/bootx64.efi from the USB drive that does boot? Is it that simple?

---

### Post by oldfred on 2017-01-14
Probably cannot copy from an install to an installer.
Each version is configured to find more boot files. 
The grub/shim versions are full grub, but the versions in the installer have only the features need to boot the install media.

But you still should be able to boot in BIOS mode from a USB flash drive.
You have to have UEFI Secure Boot off, and have to generally turn on allow USB boot and maybe some settings on mode to allow USB boot in UEFI.

Installer typically shows two boot modes in UEFI boot menu for flash drive. On is UEFI: flashdrive and the other is just flashdrive which then is BIOS boot. Flashdrive entry maybe brand or label on flash drive or its partitions.

---

### Post by sudodus on 2017-01-15
- It is easy to use 64-bit version (of standard Ubuntu or an Ubuntu flavour) for UEFI mode as well as for BIOS mode. Are your old pendrives made from 64-bit iso files or 32-bit iso files?

- It depends on the tool that you used to create the persistent live system, if your old pendrives will boot in UEFI mode.

- You can create new persistent live systems from all current Ubuntu versions and flavours and make them run in both UEFI and BIOS mode, if you use the tool mkusb according to the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

-o-

I am sorry, but I think it is easier to create new persistent live pendrives, or installed systems in pendrives (as suggested by *oldfred*), than to convert your old pendrives to UEFI mode.

If the same architecture (64-bit), I think you can save the home directories into separate partitions (with the label **home-rw** in persistent live drives) and keep your tweaks, but you will have to reinstall the program packages.

---

### Post by PopsTheSailor on 2017-01-15
Yes. I'll just have to make new ones. I'm going to mark this as solved.

---

### Post by C.S.Cameron on 2017-01-15
All the configuring you have done to the drives has been done to the casper-rw file or partition.
The rest of the drive, the squashfs file etc are the same as when the drive was built.
Casper-rw persistence files and partitions can be copied from one drive to another without loss of data. as long as the OS is the same version.
Try making your new UEFI drive and reusing your old persistence.

---

