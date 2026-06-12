---
title: "Booting Ubuntu 13.04 in EFI mode only brings up Grub CLI"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by Enkouyami on 2013-05-05
I made a EUFI bootable USB using the iso from [http://us.releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso](http://us.releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso), made sure the checksums matched, extracted it to my GPT Fat32 formatted USB with boot flagged option on, restarted my laptop and select to boot the USB in EFI mode, and was greeted by the Grub CLI. I started over again, but used Fat16 instead if FAt32 and had the same problem.

---

### Post by oldfred on 2013-05-05
It should be FAT32.
UEFI boots the installer with grub2, but it should boot if installed to flash drive correctly. 

Not sure if gpt is an issue on USB installer or not. I do use gpt on several flash drives but do not have UEFI boot as I only have BIOS.
With standard grub2 on flash drive I also have to add the bios_grub partition, but I do not know internals of installer on how it installs? Installer may convert back to MBR as that is what it expects, but then you may have backup gpt table?

I normally create grub2 bootable flash drives and now use gpt partitioning. I use grub2 loopmount to directly boot the ISO without having to install, but have no idea if that works with UEFI or not? BIOS uses grub-pc and UEFI needs grub-efi.

---

