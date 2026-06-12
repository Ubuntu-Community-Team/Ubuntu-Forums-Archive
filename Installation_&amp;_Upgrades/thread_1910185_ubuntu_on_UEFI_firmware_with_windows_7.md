---
title: "ubuntu on UEFI firmware with windows 7"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by abstractAlchemist on 2012-01-16
I've been looking around the forums lately, but there doesn't seem to be a straight forward answer to the question that I have:

Has anyone successfully, and smoothly, got a dual-boot windows 7 / ubuntu 11.10 machine on a UEFI machine?  If so, how?  Do you have wipe the entire machine clean, re-partition it?  What's the install order?  And please don't redirect me to the Ubuntu UEFI community page, because I've been there over and over again and it doesn't say very much ( as far as I can tell ).  


Forum browsing tells me this is going to be a painful process, but maybe it's just me..........

thanks for any input.

---

### Post by oldfred on 2012-01-16
I have not done it, but have been following and saving some threads as  I hope to get a new system this year with UEFI. The arch site below also have good info on grub2 with UEFI. I now use gpt from my BIOS boot and have had no issues using gparted to create gpt partitioned drives.

Because of a bug in grub overwriting the FAT32 efi partition it is better to install Ubuntu first. But partition in advance leaving the partitions Windows needs.

I have not check staus of these lately, but you need the latest version of Ubuntu to have a chance of it working.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Creating efi partition & folders in advance works.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

---

