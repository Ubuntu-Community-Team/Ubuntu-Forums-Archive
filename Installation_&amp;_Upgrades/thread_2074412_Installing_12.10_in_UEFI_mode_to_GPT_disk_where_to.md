---
title: "Installing 12.10 in UEFI mode to GPT disk: where to put the bootloader?"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by thorazine on 2012-10-21
Hi:
I'm installing 12.10 in a UEFI machine (custom built, with Asus P8Z77V-LE mobo).
Destination HDD is already partitioned in GPT mode with seveeral partitions, including EFI System Partition, BIOS Boot partition, various Windows partitions, other data partitions and one empty EXT4 formatted partition prepared for Ubuntu.
In the Partitions part of the installer after choosing "something else", I get my EFI System Partition detected and I assign the existing EXT4 partition as / to Ubuntu.
I also get my BIOS boot partition detected.
However at the bottom of the page I get a choice of where to install the bootloader, listing the whole HDD and the individual partitions.
I have a few questions:
- I thought the bootloader must always go in the EFI System Partition. Why do I have a choice?
- Is this question asking where to install the grub.efi bootloader, the grub files, or what exactly.
- I'm not sure whats the proper choice to select: the whole /dev/sda? or /dev/sda1 which happens to be my EFI partition?
- Why the installer seems to be using Bios boot partition? I thought it was noot needed when booting in UEFI mode?
- I would like to put grub files in EFI System Partition, is that posible? Do they have to be in /boot/grub?

---

### Post by oldfred on 2012-10-21
Boot loader with UEFI goes into the efi partition. Now an exception to always installing to the MBR with BIOS/MBR based systems. Not sure why you are getting a choice but it may be just how grub has always been configured to ask and they have not updated that yet.

Grub files should be in the /boot/grub folders in / (root). Unless you have a separate /boot which for most systems is not required.

If you are booting with the 64bit version the UEFI boot should offer two choices UEFI/efi or BIOS/AHCI/legacy or whatever. To install in UEFI mode you have to boot installer in UEFI mode.

With UEFI the bios-grub partition will not be used. It is required for Ubuntu to boot in BIOS mode with gpt partitioning. So you should not be using it, but as a tiny partition I would leave it. You should not see the bios-grub at all. I have BIOS and gpt and when I install grub to the MBR is just puts core.img in the bios_grub partition automatically.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by thorazine on 2012-10-22
Thanks for the answer.
I think the installer is confusing as it is, giving you a choice and then doing otherwise, I guess its not designed taking UEFI into account...
I assumed what was being asked was where to put grub files, as the grub.efi can only be in the ESP. But I was also given a choice to install to /dev/sda, that made me fear it was going to ruin my pmbr... So it didn't make sense to me at all.
Also regarding the BIOS boot partition, despite of being in uefi mode, the installer detected it and selected it no used as bios boot; I thought that was wrong so I removed it (removed the selection from use). Anyway the installer deleted it and  recreated it, in an empty spot, with fat32 and wrong guide type. That doesn't make sense too...
So there is no choice to install grub files alongside grub.efi? I think that makes more sense for uefi, to keep all the files needed to boot in there.

---

### Post by oldfred on 2012-10-22
If grub is trying to use the bios_boot partition then you must have booted in the BIOS mode. Then it will ask where to install as you still with BIOS install grub2's boot loader to the MBR.

The efi partition is just the new MBR, not intended as a boot partition even though it has the "boot" flag. That is just to show it is the efi partition in the UEFI definition.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by darkod on 2012-10-22
Watch out for two things:
1. Boards seem to have not only UEFI or BIOS boot options, but also UEFI & BIOS which means both at the same time. In my opinion, that can create even more confusion (as if there is not enough confusion about uefi as it is :) ). So, if possible, set it only to legacy boot, or only to uefi boot. Not the mixed.

2. Whether ubuntu will try to install in bios or uefi mode depends how you boot the cd. Note what oldfred said earlier. You will have to boot the cd in uefi mode if you want uefi installation.

Otherwise, if you boot in standard bios mode it will try to install in standard mode using the bios_grub even if you have UEFI boot enabled in bios.

Boards that support uefi have two "different" devices for the dvd drive:
"standard" dvd drive
uefi dvd drive

Be careful which one you select when booting from, so that the ubuntu installer starts in bios or uefi mode.

---

### Post by thorazine on 2012-10-22
I'm sure I was booting in UEFI mode, I chose the UEFI entry in the bios boot manager, I have EFI: in dmesg and /sys/firmware/efi/vars exist.
And in the end I got the installer pur grub.efi right in ESP, however for some reason I was given the choice to where put the bootloader, and the installer took my bios boot partition even though is not needed, not only that, when I disabled its use, it erased and recreated it for no apparent reason.
Unless there is something else that is tricking the installer or confusing it somehow?

As for grub files location I think it makes perfect sense to have all the files required to boot there, as it is a real partition, not just a MBR, you can put any files there and being fat32 you can access them for pretty much everything, including a UEFI shell for emergency (which cant read ext4 from what I know). At least having the choice of where to put them...

I'll post the link to BootInfo as requested later, but I'm not sure if its useful for diagnosing this issue as I redid the installation a second time.

---

### Post by oldfred on 2012-10-22
All Linux system files have to be in a Linux formatted partition. Neither FAT32 nor NTFS support Linux file permissions and ownership. So Windows formats can only be used for data. The efi partition seems to be an exception but that is a requirement of UEFI not Windows nor Linux.

---

### Post by thorazine on 2012-10-24
Here its the boot report in case it may be useful to diagnose this strange behaviour:

[http://paste.ubuntu.com/1302607/]("http://paste.ubuntu.com/1302607/")

BTW, reading a bit the Arch Linux Wiki it seems its perfectly posible to have grub installed to the EFI System Partition, when doing it manually, apparently its just another grub's option, so its not really needed to have all grub files in root partition:

[https://wiki.archlinux.org/index.php/GRUB#Install_to_UEFI_SYSTEM_PARTITION]("https://wiki.archlinux.org/index.php/GRUB#Install_to_UEFI_SYSTEM_PARTITION")

I personally find this option much more reasonable when multibooting when you can access grub's configuration easily from any OS that supports fat32.

---

### Post by YannBuntu on 2012-10-24
> **thorazine said:**
> I was given the choice to where put the bootloader

I think that's a bug of the installer (Ubiquity). When it installs grub-efi, it shouldn't give choice for bootloader location (except if there are several ESPs).
You should report it here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug) (and tell us the link)

> **thorazine said:**
> the installer took my bios boot partition even though is not needed, not only that, when I disabled its use, it erased and recreated it for no apparent reason.
Unless there is something else that is tricking the installer or confusing it somehow?

That looks like another bug of the installer. It shouldn't create any BIOS-Boot partition when using grub-efi.
Did you format the BIOS-Boot partition before reinstalling Ubuntu?

---

