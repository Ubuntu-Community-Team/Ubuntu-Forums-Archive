---
title: "Help!!! I installed bootloader on usb install drive, not on my hard drive sda :("
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by RGVsUrTexas on 2015-03-30
Hi,

Hope someone can help me with a remedy to my noobish mistakes.  My install works great as long as I have the usb attached to my pc.  Well, I want to boot from my hard drive.  

From the boot repair disk tool

No boot loader is installed in the MBR of /dev/sda
Syslinux MBR is installed in the MBR of /dev/sdc

1:
File system: vfat
Boot Sector Type: FAT 32
Boot Sector info: No errors....
Operating system:
Boot files:    /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi
                  /EFI/ubuntu/shimx64.efi

2:
File system: ext2
Boot Sector Type: 
Boot Sector info:
Operating system:
Boot files:    /grub/grub.cfg

3:
File System: crypto_luks
Boot sector type: unknown
Boot sector info:

1:
File system: vfat
Boot Sector type: Syslinux ...
Boot Sector info: syslinux looks at sector 32816 of /dev/sdc1 for its second stage...
Operating system:
Boot files:    /boot/grub/grub.cfg /casper/vmlinuz.efi
                 /EFI/BOOT/grubx64.efi


I just wanna rebuild grub to pick up the sda hard drive.

Thanks,

Andy

---

### Post by grahammechanical on 2015-03-30
Load into Ubuntu. Open a terminal and run

```
sudo grub-install /dev/sda
```

Regards

---

### Post by sammiev on 2015-03-30
> **grahammechanical said:**
> Load into Ubuntu. Open a terminal and run

```
sudo grub-install /dev/sda
```

Regards

+1

also 

```
sudo update-grub
```

---

### Post by oldfred on 2015-03-30
Are you booting install or live installer?
You show UEFI install with LVM and full drive encryption.
And you have grub in the efi partition on hard drive.

If you go into UEFI boot menu or use one time boot key does it show ubuntu as a boot choice?

---

### Post by RGVsUrTexas on 2015-03-30
Thanks so much for the quick response.  I am using the boot repair tool interface, and when i type the instructions the following occurs:

Installing for i386-pc platform
grub-install:error:failed to get canonical path of '/cow'

Andy

---

### Post by oldfred on 2015-03-31
You are installing the CSM/BIOS version of grub. It you really want BIOS not UEFI then you have to create a bios_grub partition. And you are installing to installer as that is the /cow error, not to hard drive.

But since you have the efi partition, I expect you really want the UEFI version which should be grub-efi-amd64. 

How you boot installer or Boot-Repair UEFI or BIOS is how it works, so reboot flash drive with Boot-Repair in UEFI mode.

---

### Post by RGVsUrTexas on 2015-03-31
Thanks that worked !!!!

Andy

---

