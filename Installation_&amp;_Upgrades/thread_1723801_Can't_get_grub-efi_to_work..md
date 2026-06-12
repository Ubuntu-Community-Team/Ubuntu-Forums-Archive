---
title: "Can't get grub-efi to work."
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by xdominex on 2011-04-07
Hello, everyone!
After much googling and trial-and-error, I have finally decided to ask about this problem. I have an hp tm2t-1100, a computer that supports efi/uefi booting. However, when I install grub-efi, it installs itself to my hard drive (even though I'm using GPT!) and sets itself up to boot BIOS-mode and then EMULATE EFI. How can I get grub to install to an EFI system partition? I know I need a FAT32 partition named HP_TOOLS and a /boot/efi/ directory on it. I already have those things, but I cannot figure out for the life of me how to get grub-efi to install for a real actual efi-boot instead of what it is doing now (installing like normal grub and emulating efi).

---

### Post by srs5694 on 2011-04-07
> **xdominex said:**
> Hello, everyone!
After much googling and trial-and-error, I have finally decided to ask about this problem. I have an hp tm2t-1100, a computer that supports efi/uefi booting. However, when I install grub-efi, it installs itself to my hard drive (even though I'm using GPT!)

Where else would it install? I suspect you mean it's installing in the /boot directory, but the details even there are critically important, so you'll have to be more precise about where it's putting files. (FWIW, on my EFI-booting Mac, the grub-efi-ia32 package doesn't put anything in /boot, but running grub-install does, IIRC.)

> and sets itself up to boot BIOS-mode and then EMULATE EFI.

I suspect you're misinterpreting or misunderstanding something. Whether the computer boots in EFI mode or in BIOS mode is *entirely* under the control of the firmware. GRUB has nothing to do with this. You must install the appropriate version of GRUB (for BIOS or EFI) based on the boot mode you select in the BIOS. If you select the wrong version of GRUB, the computer won't boot at all (unless perhaps the firmware has a fallback option to try both booting styles).

> How can I get grub to install to an EFI system partition? I know I need a FAT32 partition named HP_TOOLS and a /boot/efi/ directory on it.

Not quite. You need a FAT32 partition that's of GUID type C12A7328-F81F-11D2-BA4B-00A0C93EC93B. This partition is identified in GNU Parted, GParted, and other libparted-based tools as having the "boot flag" set (although this re-use of MBR terminology is confusing at best, since it's in no way analogous to a boot flag on an MBR partition); and in gdisk, it's identified as a partition of type EF00. The name of the partition is irrelevant. IIRC, HP uses a partition with the name of HP_TOOLS to store some HP-specific software, but AFAIK this has nothing to do with an EFI System Partition. (OTOH, I don't own an HP computer, so I could well be mistaken about this.)

Although this practice doesn't seem to be universal, the EFI System Partition is often *mounted at* /boot/efi in the Linux directory tree. The partition does not normally have a directory of that name on it -- but confusingly, it does have a directory called EFI, and that directory usually has a subdirectory called BOOT. Thus, your system may have a directory called /boot/efi/EFI/BOOT. (The EFI/BOOT directory on the EFI System Partition might be named in lowercase; as it's FAT, case is irrelevant.)

> I already have those things, but I cannot figure out for the life of me how to get grub-efi to install for a real actual efi-boot instead of what it is doing now (installing like normal grub and emulating efi).

I don't recall offhand exactly where grub-install put its files when I ran it on various EFI test installations. I believe the details varied depending on how I obtained GRUB (building it myself vs. installing a binary). Ideally, "grub-install /dev/sda" should do the trick, but that might depend on the EFI System Partition being mounted at /boot/efi. I've found that building GRUB myself seems to be a bit more reliable than relying on pre-built packages. For instructions on that approach, see [this Web page.](http://grub.enbug.org/TestingOnMacbook)

---

### Post by xdominex on 2011-04-08
First of all, many thanks for replying and taking the time to address my problem! When I said it installs itself to my main hard drive, I meant directly to a "boot sector" exactly like it would if it was mbr setup, meaning it initializes directly off of the hard drive instead of an actual partition. Sorry for the confusion there; I was rather nebulous on that one.

> You need a FAT32 partition that's of GUID type C12A7328-F81F-11D2-BA4B-00A0C93EC93B. This partition is identified in GNU Parted, GParted, and other libparted-based tools as having the "boot flag" set (although this re-use of MBR terminology is confusing at best, since it's in no way analogous to a boot flag on an MBR partition); and in gdisk, it's identified as a partition of type EF00. The name of the partition is irrelevant. IIRC, HP uses a partition with the name of HP_TOOLS to store some HP-specific software, but AFAIK this has nothing to do with an EFI System Partition.
I have an official HP pdf about the HP_TOOLS partition. The following information in this paragraph comes directly from that pdf. The "BIOS" (I'm sure they use this terminology universally to confusion in consumers and their Indian tech support employees) on my computer will ONLY do an EFI-boot from a fat32 partition named HP_TOOLS. It searches for the HP_TOOLS partition and looks in it for an EFI application to load. If it cannot find an EFI application inside a "HP_TOOLS" partition, it falls back on a traditional BIOS-mode boot.

> Although this practice doesn't seem to be universal, the EFI System Partition is often mounted at /boot/efi in the Linux directory tree. The partition does not normally have a directory of that name on it -- but confusingly, it does have a directory called EFI, and that directory usually has a subdirectory called BOOT. 
I actually already have my efi partition, a FAT32 GPT partition flagged "boot," mounted at /boot/efi, though the directory I created in it was "/boot/efi" instead of "/efi/boot" (meaning an ubuntu directory of /boot/efi/boot/efi rather than the "/boot/efi/efi/boot" directory you said I should have). I will change that now to see if it helps somehow.

> I've found that building GRUB myself seems to be a bit more reliable than relying on pre-built packages. For instructions on that approach, see this Web page.
I actually have already looked at that page multiple times but wasn't sure if I would have to write the whole grub.conf on my own or only make tweaks to it or what. I am willing to remain open-minded to whatever instruction or recommendation you might have for me.

---

### Post by srs5694 on 2011-04-08
> **xdominex said:**
> First of all, many thanks for replying and taking the time to address my problem! When I said it installs itself to my main hard drive, I meant directly to a "boot sector" exactly like it would if it was mbr setup, meaning it initializes directly off of the hard drive instead of an actual partition. Sorry for the confusion there; I was rather nebulous on that one.

It's still unclear to me what's going on with your system. What command did you use to install GRUB, how do you know that it wrote directly to a "boot sector," and what "boot sector" did it install to (the MBR, the partition boot sector, or something else)?

> I have an official HP pdf about the HP_TOOLS partition. The following information in this paragraph comes directly from that pdf. The "BIOS" (I'm sure they use this terminology universally to confusion in consumers and their Indian tech support employees) on my computer will ONLY do an EFI-boot from a fat32 partition named HP_TOOLS. It searches for the HP_TOOLS partition and looks in it for an EFI application to load. If it cannot find an EFI application inside a "HP_TOOLS" partition, it falls back on a traditional BIOS-mode boot.

I'm a bit suspicious of at least some of this, since I don't recall anything in the EFI specification about an option to limit the boot options by the name of the partition. OTOH, I haven't studied that part of the EFI spec in any depth, and HP could have violated the spec as it saw fit.

There's also the question of what "name" is meant -- the GPT partition name or the filesystem name. If the PDF you've quoted is correct, it's conceivable that your computer is not booting the way you expect because you set the filesystem name but the EFI is looking at the partition name or vice-versa. You can change a FAT filesystem's name with the dosfslabel utility, and you can change a GPT partition's name using the gdisk or sgdisk utility.

---

### Post by xdominex on 2011-04-08
It is installed to a master boot record on my GPT tablet. I didn't even think this was possible, but it appears to be so. I know this to be true because the "grub rescue" deal comes up when I wipe all of my partitions off of the hard drive. Also, when I look in my /boot/grub folder, it has files for grub to initiate EFI emulation instead of an EFI application file (*.efi).

I installed grub-efi from synaptic package manager.

The pdf I mentioned in my previous post is attached to this one.

---

