---
title: "How to add EFI but keep existing legacy boot capability (hybrid boot)"
date: 2015-10-10
forum: Installation &amp; Upgrades
---

### Post by ed-agoff on 2015-10-10
I have created a bootable USB installation of 12.04.5 using an MBR-formatted stick and legacy grub installed to the MBR. I've got as far as understanding I need a FAT32 partition for /boot/efi, and found various instructions on how to enable/repair legacy or EFI boot, but performing one always seems to corrupt the other ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing), et al). 

Given my existing legacy bootable stick, two partitions, sda1 = 200MB FAT32, sda2 = ext4,

How to I add EFI and retain legacy boot capability?

---

### Post by oldfred on 2015-10-10
Better to use gpt partitioning. UEFI has to boot from a FAT32 partition and UEFI normally is gpt. Ubuntu installer often is MBR(msdos) with just one FAT32 partition and that will work for many systems. We see a few that UEFI only boots from gpt.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by sudodus on 2015-10-10
Welcome to the Ubuntu Forums :-)

Are you talking about an installed system or a persistent live system? (See the following link for details about these different kinds of systems)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

How do you intend to use your system?

---

### Post by ed-agoff on 2015-10-10
sudodus, I'm talking about an installed system.

Thanks, oldfred! Your response was very informative. And the last link was excellent:
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

I  had to move to 14.04, since the 12.04 grub-install didn't include the  efi options, and the steps in link above ("Add an ESP to an existing installation with MBR") worked like a charm!

---

