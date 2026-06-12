---
title: "W8 , Ubuntu and gpt ssd"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by thomas_j_marshall2 on 2014-12-05
Hi.  I have been dual-booting Windows 8 & Ubuntu 14.04 for a while.  I couldn't get grub to work so I used Easybcd, it was a bit of a fudge but worked.  Just installed a 240 gig SSD, 2 partitions, W8 on one so Ubutnu to go on the other.  The unused partition was formatted NTFS but I was unable to format within the Ubuntu installer.  (Should have said it's gpt)

The option to change partition structure is greyed out, do I need to set up the partition structure in windows first?

Also, where should grub go in the installation?  In the bios, and at install, there is a partition marked windows bootloader, there, or on the remaining partition?  I want to be able to boot the two from grub, not using Easybcd.


Thanks.

---

### Post by ubfan1 on 2014-12-05
I do like to set up my partitions and format them with the filesystem I want (ext4 usually) before running the installer. gdisk on your live media should allow you to partition and then you may add the filesystem with mke2fs.  The way UEFI works, is the bootoaders are just put into a FAT filesystem on a bootable partition, so the Ubuntu bootloaders (shimx64.efi/grubx63.efi) should go into /EFI/ubuntu , a directory totally separate from the Windows bootloaders, so there is no interference.  When you run the installer, the bootloader location seems to want to default to that location anyway (which is what you want if you only have one disk).  Grub should work in either secure or not secure boot, UEFI mode.

---

### Post by oldfred on 2014-12-05
When you say one partition for Windows, did you install in UEFI mode? Windows only boots from gpt partitioned drives with UEFI but requires several partitions.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

For both Windows & Ubuntu you have to use 64 bit versions and how you boot installer UEFI or BIOS will be how it installs. 
But Windows only boots from gpt with UEFI. 
And both Windows & Ubuntu only boot from MBR(msdos) with BIOS.
Ubuntu confuses it a bit as it can boot with either UEFI or BIOS from a gpt drive.

---

### Post by thomas_j_marshall2 on 2014-12-05
> **oldfred said:**
> When you say one partition for Windows, did you install in UEFI mode? Windows only boots from gpt partitioned drives with UEFI but requires several partitions.
Yes, UEFI, windows boots OK from the new disk.

---

### Post by thomas_j_marshall2 on 2014-12-05
> **ubfan1 said:**
> I do like to set up my partitions and format them with the filesystem I want (ext4 usually) before running the installer. gdisk on your live media should allow you to partition and then you may add the filesystem with mke2fs.  The way UEFI works, is the bootoaders are just put into a FAT filesystem on a bootable partition, so the Ubuntu bootloaders (shimx64.efi/grubx63.efi) should go into /EFI/ubuntu , a directory totally separate from the Windows bootloaders, so there is no interference.  When you run the installer, the bootloader location seems to want to default to that location anyway (which is what you want if you only have one disk).  Grub should work in either secure or not secure boot, UEFI mode.That's what I'm not sure about.  So basically grub or the boot partition goes on the new Ubuintu partition?  I'm just wondering how the bios or uefi picks where to boot from if there are two locations, one on the windows partition and the other on Ubuntu.

---

### Post by oldfred on 2014-12-05
With BIOS, there was only one choice and that was whatever was in MBR.

But with UEFI you can install as many operating systems as you want. And each had a folder in the efi partition. And UEFI is a boot manager that lets you select which system to boot. It is like having multiple MBRs or a multiple drive system. All systems share one efi partition per device. But you can and generally should have an efi partition on every drive or device that you may ever want to boot from.

But like BIOS, only part of the boot process is in the efi folder. You install grub2's boot loader to the drive and it defaults to the efi partition if installing in UEFI mode. But much of grub, menus, configuration files, scripts are all in the Ubuntu partition.

But some vendors are violating UEFI spec and making it only boot (or only default boot) a system with Windows in description. 
So many different work arounds have been found and depending on brand, model and perhaps how you have installed which work around is best.

---

### Post by thomas_j_marshall2 on 2014-12-05
> **oldfred said:**
> With BIOS, there was only one choice and that was whatever was in MBR.

But with UEFI you can install as many operating systems as you want. And each had a folder in the efi partition. And UEFI is a boot manager that lets you select which system to boot. It is like having multiple MBRs or a multiple drive system. All systems share one efi partition per device. But you can and generally should have an efi partition on every drive or device that you may ever want to boot from.

But like BIOS, only part of the boot process is in the efi folder. You install grub2's boot loader to the drive and it defaults to the efi partition if installing in UEFI mode. But much of grub, menus, configuration files, scripts are all in the Ubuntu partition.Sorry for keeping on but I just want to get it clear for myself.  If I just install Ubuntu as I usually would, i.e. set up boot, /, home, swap, the installer will put a folder in EFI?

---

### Post by oldfred on 2014-12-05
Yes.

With most desktops you do not need a separate /boot partition. If a server type install with RAID or LVM then you may need that. Do not confuse the efi partition with a /boot partition. They are totally different.

Depending on where it is mounted, these are the folders for a dual Windows & ubuntu efi partition:
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

In Ubuntu the efi partition is mounted at /boot/efi, so the full path is /boot/efi/EFI/ubuntu.

---

### Post by thomas_j_marshall2 on 2014-12-05
> **oldfred said:**
> Yes.

With most desktops you do not need a separate /boot partition. If a server type install with RAID or LVM then you may need that. Do not confuse the efi partition with a /boot partition. They are totally different.

Depending on where it is mounted, these are the folders for a dual Windows & ubuntu efi partition:
 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

In Ubuntu the efi partition is mounted at /boot/efi, so the full path is /boot/efi/EFI/ubuntu.Thank you very much.  Think I've got it now!  I'll let you know how it goes.

---

### Post by thomas_j_marshall2 on 2014-12-06
> **thomas_j_marshall2 said:**
> Thank you very much.  Think I've got it now!  I'll let you know how it goes.Well I have managed to install Ubuntu alongside W8 and it appears in the boot menu.  However, I think it's the wrong one!  The efi appears to be booting my old installation of ubuntu which I still have on another disk.  How can I point it to the new install on the SSD?

---

### Post by thomas_j_marshall2 on 2014-12-06
> **thomas_j_marshall2 said:**
> Well I have managed to install Ubuntu alongside W8 and it appears in the boot menu.  However, I think it's the wrong one!  The efi appears to be booting my old installation of ubuntu which I still have on another disk.  How can I point it to the new install on the SSD?Managed to solve it by running update grub.

---

### Post by oldfred on 2014-12-06
Post these, if longer use code tags or # icon in advanced editor:
       modprobe efivars
sudo efibootmgr -v

cat /boot/efi/EFI/ubuntu/grub.cfg
      
 sudo blkid -c /dev/null -o list

mount

---

