---
title: "Screwed up Windows Boot-loader"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by ALinuxWindowsBalance on 2012-11-26
Hey, all. This was MY mistake and I know exactly what I did wrong, now I'm stuck with a broken 12.10.
My Dell XPS 8500 has a 1TB internal HDD.

Alright, bought a new XPS 8500, and Set up Win 8. Very beautiful, and clean. For some reason, I decided I should have Linux running in there somewhere. So, 12.10 Came in through my ODD and I started through the installation. 

**Okay, developers, this is where you pay attention.**

Ubuntu 12.10 DOES NOT understand EFI/Windows 8. Please Fix.


Beforehand I reduced the NTFS with Win 8 in Windows to reduce errors.
No OS detected, so I make a small partition, 250GB, and install it there. 

**I forgot to change where the GRUB was installed. Now I pay for it by Windows not being able to boot.**

I installed it in the MBR instead of the / partition. 
        I was able to open the GRUB menu, but the Windows UEFI wasn't there.

I haven't figured out how exactly to add an EFI in the GRUB, or anything, for that manner.

**I need either directions on how to add a selection to the GRUB, or a link to a new bootloader.**

I will not delete the Win 8 partition, as I have no backup disks. (Thanks a lot, Dell!)
I do, however, have Drivers+Utilites on a disk, but they are for DOS.

Please help me. And soon, because I'm on a time crunch.

---

### Post by oldfred on 2012-11-26
Ubuntu 12.10 64 bit does correctly install to UEFI with secure boot.  Okay only on some as some vendors have not correctly implemented UEFI and grub does not have work arounds for those.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    
But you have to boot the Ubuntu liveCD or USB installer in UEFI mode not BIOS mode. It sounds like you booted in BIOS/legacy/AHCI mode not UEFI.

Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi. Grub2's os-prober also has a bug in it only creates a BIOS type chain load boot for Windows not a UEFI boot. But Boot-Repair can also fix that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)    
       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)

    UEFI installs in BIOS, Boot-Repair to fix
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)
[http://ubuntuforums.org/showthread.php?t=2058453](http://ubuntuforums.org/showthread.php?t=2058453)

    [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

