---
title: "USB full install of Ubuntu 13.04 64-bit wont boot from USB when boot mod set to UEFI"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by lijo2 on 2013-10-12
I have installed Ubuntu 13.04 amd64(full install) to a 16GB USB FLash Drive by booting into a live USB made from the ISO of Ubuntu 13.04 itself, using Universal USB Installer utility. I did this on my VAIO SVS13112EN Laptop with Windows 8 pro OS. The problem is that I cannot boot into my full install Ubuntu when the boot mode in the bios setting is set to UEFI. If I change the setting to legacy my full install boots up perfectly. But the Live usb of the same which I used to make the full install is able to boot into Ubuntu. I would like to know how I can get the full install USB to boot even when the boot mode is set to UEFI, because my Win8 OS does not boot when in Legacy Mode. Therefore I have to keep changing the boot mode everytime I need to boot Windows 8 or Ubuntu. I am new to Linux, but I am keen on becomming familiar with it. So please help me out asap. Thanks.

---

### Post by ajgreeny on 2013-10-12
If I understand UEFI properly, you need to boot the live system in UEFI mode then also install in UEFI mode as well or you will experience the problems you are seeing.

See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by oldfred on 2013-10-12
How you boot installer is how it installs.

While Boot-Repair can convert a BIOS boot install to UEFI boot, you would have to partitioned with gpt and have an efi partition as the first partition. 
The ISO installer has an efi partition that is used when booting the ISO in UEFI mode, similarly. 

I do not have UEFI but have partitioned my 16 & 32GB flash drives with gpt and with BIOS I have to have the bios_grub partition to boot. But since I plan on UEFI system soon, I left space for an efi partition at beginning of flash drive.

If you have a flash drive and it is gpt with an efi partition you can directly install grub-efi into it.
 sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable

While you can install with UEFI with secure boot, UEFI without secure boot or BIOS you can use gpt partitioning on a flash drive with all three types of installs.

Other info I saved, signed versions only required if booting with secure boot on:

 Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
If you are unable to launch UEFI Shell from the firmware directly using any of the above mentioned methods, create a FAT32 USB pen drive with Shell.efi copied as (USB)/efi/boot/bootx64.efi . This USB should come up in the firmware boot menu. Launching this option will launch the UEFI Shell for you.
Manually copy efi files to efi partition on flash drive. Toshiba Satellite S855-5378
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg

---

