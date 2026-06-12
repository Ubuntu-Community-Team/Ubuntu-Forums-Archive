---
title: "Boot Ubuntu Live from Hard disk"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by K_Dase on 2015-08-08
Hi,

I am using Windows 8.1 at the moment. I have shrink my C drive (Windows comes pre-installed in my laptop) and allotted 15Gb of free space for using Ubuntu.

I don't want to go the usual way of installing Ubuntu, but rather would like to:

1. Create mkfs.ext4 on the free space. 
2. Copy the files from Live USB to Stable Install.
3. Modify the EFI by adding grub loader in Windows EFI file. 

So, my question is, what all files do I need to add/copy to ext4 formatted free space on the drive? Do I also need to create SWAP partition in that case?
And using EFI grub loader from say Fedora to Ubuntu will work and vice versa? 

I am somewhat aware that we need to few files like /isolinux/vmlinuz0,  /isolinux/initrd0.img, but as a general rule, how do I bypass the normal installation and boot the live cd as plain installation mode. 

Thank you.

---

### Post by oldfred on 2015-08-08
I have no idea how to install a grub2 boot loader from Windows. You can from live installer, but then you have created live installer. Or from any install of Linux.

I do regularly install from hard drive and have ISO partitions on each drive to install ISO to other drive. I also have ISO on flash drives to boot directly with grub.  And have used both BIOS & UEFI to boot ISO.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

With UEFI I cannot get grub to install to sdb or flash drive when doing full installs. I quickly learned to backup my efi partition on sda as it gets over written with every install. My main working install of Ubuntu is in sda's ESP. But so far with same versions of grub the only difference has been the tiny  grub.cfg in /EFI/ubuntu that is just a configfile entry to find the full grub.cfg in the install.

I use these entries and have two ISO partitions one on each drive. And I have the configfile as my actual ISO boot. Then I can update/add/change ISO without having to run sudo update-grub. I always forgot to do that when I directly booted ISO from main grub.cfg.

```
menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

menuentry 'Live ISOs on HDD (boot on SSD)' {
configfile (hd1,6)/livecdimage.cfg
} 

```

Boot drive is always hd0, when using BIOS, I had to edit typical example above if I have a grub install on a second or third drive, and then if manually booting sometimes had to manually edit the hdX entry to correct drive as seen by BIOS/grub which is not same as Ubuntu.

my livecdimage.cfg is just like all the examples in ISOBoot/examples link above and is in ISO partition.

---

