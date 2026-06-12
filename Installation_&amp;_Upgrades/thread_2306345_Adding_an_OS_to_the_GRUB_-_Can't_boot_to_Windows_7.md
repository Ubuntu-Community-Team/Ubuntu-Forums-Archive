---
title: "Adding an OS to the GRUB - Can't boot to Windows 7"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by Eros_Vidal_Tagina on 2015-12-14
Greetings!

I'm going back into Ubuntu and found out I can't do anymore the easy dual-boot (on Legacy only mobos was easy, now with a new UEFI and Legacy mobo I'm in an uncomfortable situation)

I had Windows 7 installed on this new rig and wanted to do a dual boot to Ubuntu, got the UEFI warning, said "go back" it installed anyways, and now I can't boot Windows.

I got a 500gb hdd and only dedicated 50gb to Ubuntu (since I was testing the new release)

Here's the info of sudo update-grub

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
/etc/grub.d/40_custom.save: 1: /etc/grub.d/40_custom.save: menuentry: not found
/etc/grub.d/40_custom.save.1: 1: /etc/grub.d/40_custom.save.1: menuentry: not found
insmod: ERROR: could not load module part_msdos: No such file or directory
insmod: ERROR: could not load module ntfs: No such file or directory
/etc/grub.d/40_custom.save.1: 5: /etc/grub.d/40_custom.save.1: chainloader: not found
/etc/grub.d/40_custom.save.1: 6: /etc/grub.d/40_custom.save.1: Syntax error: "}" unexpected



It finds windows 7 but doesn't add it to the menu, how can I add it (Already tried with the terminal but don't know how to do the save of the new line)

I really need to do a dual boot (or get Windows 7 to show up on GRUB) because everyone else who might use the computer only knows how to handle Windows.

I hope anyone can help me because otherwise I would have to wipe out the drive and start over

---

### Post by oldfred on 2015-12-14
If you forced Ubuntu to install in UEFI mode, it probably converted to gpt partitions.
But if Windows is in BIOS mode it only boots from MBR(msdos) partitions. 
Grub will only dual boot systems installed in same boot mode either both UEFI or both BIOS.

Best to see all details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

