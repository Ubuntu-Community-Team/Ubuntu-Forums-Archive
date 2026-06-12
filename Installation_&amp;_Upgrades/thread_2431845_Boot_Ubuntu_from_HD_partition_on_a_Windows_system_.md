---
title: "Boot Ubuntu from HD partition on a Windows system? (help with GRUB)"
date: 2019-11-22
forum: Installation &amp; Upgrades
---

### Post by gilius2 on 2019-11-22
When I write the ISO to USB then it automatically created the EFI folder - all to a single partition:
[IMG]https://i.postimg.cc/MGP5bFkx/iso1.png[/IMG]

However, if I simply extract everything to a single partition then I have to extract the EFI from the [BOOT] Folder and move it to the root.

When I boot from USB I get to the install menu; but when I add \EFI\BOOT\BOOTAA64.EFI as a boot device from HD partition I get the Grub prompt instead.

How can I make the EFI file "chainload"(?) to the install menu instead of giving me a Grub prompt? And how can I achieve this without using any apps - only the command line?

Why does writing to USB chainload correctly - but simply extracting the files lead to a Grub prompt?

---

### Post by oldfred on 2019-11-22
What is \EFI\BOOT\BOOTAA64.EFI ?
Normal boot file for flash drive or hard drive is /EFI/Boot/bootx64.efi. And version on flash drive is a copy of a limited grub just to boot flash drive.

Full install of grub to a flash drive has a full copy of shimx64.efi as bootx64.efi and internally also needs /EFI/ubuntu for more boot files.

I used to use the extract method, but newest Ubuntu now has some links and links are not allowed with FAT32. But UEFI has to boot from FAT32. 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1849534)

For an internal drive, you have to have an ESP - efi system partition. And then add UEFI boot entries into UEFI.
If booting the hard drive entry, that is also a fallback entry that is like the flash drive entry. /EFI/Boot/bootx64.efi. But standard install has a 3 line grub.cfg that uses configfile to load the full grub install. With flash drive that grub is the boot of the installer files.

Example of configfile:
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13788092#post13788092](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13788092#post13788092)
[https://askubuntu.com/questions/958760/what-does-gpt7-refers-to-in-my-grub-cfg](https://askubuntu.com/questions/958760/what-does-gpt7-refers-to-in-my-grub-cfg)

---

### Post by gilius2 on 2019-11-22
The [COLOR=#000000]\EFI\BOOT\BOOTAA64.EFI is the ARM64 counterpart to [/COLOR][COLOR=#000000]/EFI/Boot/bootx64.efi (AMD64)

but the architecture doesn't matter so much because the Windows EFI Boot Loader handles them in the same way.

There's no other EFI files on that live ISO, so that should be the gateway to the install menu:
[/COLOR][https://ubuntu.com/download/server/arm](https://ubuntu.com/download/server/arm)

The single partition is indeed FAT32

> [COLOR=#000000]But standard install has a 3 line grub.cfg that uses configfile to load the full grub install. With flash drive that grub is the boot of the installer files.[/COLOR][COLOR=#000000]
That's the part that interests me. I need to learn how the EFI file can load that grub installer - perhaps via the Grub prompt? You see I don't know anything about grub; I only know how to boot stray windows partitions.
[/COLOR][IMG]https://i.postimg.cc/PxbPGKZc/grub.png[/IMG]

---

### Post by gilius2 on 2019-11-22
I followed this guide:
[https://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-prompt-shows-up-instead](https://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-prompt-shows-up-instead)

But then encountered this error:
[https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](https://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue)

I think it might be because the FAT32 partition is on a GPT disk instead of MBR?

---

### Post by oldfred on 2019-11-22
With PC & Mac the ESP - efi system partition must be FAT32 for UEFI to find it.
Windows requires gpt for UEFI boot.
Ubuntu recommends gpt, but does let you install to MBR with either BIOS or UEFI.

Not sure then about ARM and what its configuration is.

---

### Post by gilius2 on 2019-11-23
Don't forget I was trying to boot the live CD from HD - not the actual operating system. However, I can now confirm it works via MBR - and GPT was indeed the problem. In the process I've also learnt a bit about GRUB, so that when it comes to booting the actual operating system by way of an EFI file that chainloads to GRUB then I'll hopefully be able to expand on this exercise to achieve that. And as you said: maybe GPT will then become an option for the main OS.

---

