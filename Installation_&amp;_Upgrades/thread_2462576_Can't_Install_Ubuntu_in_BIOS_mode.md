---
title: "Can't Install Ubuntu in BIOS mode"
date: 2021-05-23
forum: Installation &amp; Upgrades
---

### Post by gasparb123 on 2021-05-23
Hello, I've recently acquired and restored an old computer with an Intel D946GZIS motherboard with a Core 2 Duo E4400, installed the max 4GB of DDR2 667 memory, and a Kingston SSD. The motherboard is circa 2006/07, so I am sure it does not support UEFI (corroborated with motherboard manual and BIOS settings). I created a BIOS install USB of Ubuntu 20.04 with Rufus, and attempted to install it on this computer, but I ran into issues. The live USB works and I am able to enter the OS, install it completely and after instalation it prompts me to remove the USB drive and press enter, as usual. 

The problem is that upon reboot the system throws me a black screen and a message saying that no boot drive has been found. I reinserted the USB drive and entered through the Live OS, and it has installed correctly as far as I can tell. Although I have my doubts if the OS has been installed in BIOS mode or not, given that there is an EFI folder in the boot menu, and the automatic install says that 2 partitions will be created: the normal home partition and a ESP partiton. I've searched and discovered that this partition is related to UEFI. 

The question is why is Ubuntu assuming my computer is UEFI compatible, and how can I make it to force a BIOS/Legacy instalation? 

Any help will be appreciated, and thanks in advance.

P.S I've tried other flavors of Ubuntu and I have had the same problems

---

### Post by tea for one on 2021-05-23
After you have booted Ubuntu in a live session, you can double-check if you have booted in UEFI or Legacy mode by opening a terminal and entering:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

I should have added the observation that:-

Boot in Legacy mode = Install in Legacy mode
Boot in UEFI mode = Install in UEFI mode

---

### Post by grahammechanical on 2021-05-23
> The question is why is Ubuntu assuming my computer is UEFI compatible,  and how can I make it to force a BIOS/Legacy instalation? 

This is my guess. The Ubuntu installer is giving the SSD a GPT partition table and not an MBR partition table. And that is why you have an EFI partition. With a GUID Partition Table (GPT) and a BIOS motherboard we get both a BIOS boot partition and an EFI partition. 

I know this is true because I have a BIOS motherboard as old as your motherboard. I have two hard discs. One is has a GPT partition table with both a BIOS boot partition and an EFI partition. The other hard disc has a Master Boot Record (MBR) partition table and the boot files are in a small space at the front of the drive called the MBR and not in a partition. The MBR does not show up in a disc/partition manager examining a MBR partition table hard drive.

Please do not think of changing the type of partition table from GPT to MBR as GPT is compatible with a BIOS motherboard and is better than an MBR partition table. Why this is so is another story.

So, I suggest looking elsewhere for this "no boot drive found" message

Regards

---

### Post by oldfred on 2021-05-23
There was some discussion that newest Ubuntu creates an ESP - efi system partition even on BIOS/MBR installs.
Better to use gpt anyway.

How you create installer with Rufus, is then how it installs. You want the BIOS/MBR or CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

My very old laptop with core2 duo with 1.5GB of RAM used to install full Ubuntu but was so slow as to be unusable. I normally converted to fallback/flashback gui which is another lightweight gui. I also used that with my desktops.
I tried installing 20.04 Ubuntu on laptop and it would not install. I did install server & add fallback, but huge hassle getting it right.
Later I converted my desktops to Kubuntu which is not considered as lighter weight. But I tried Kubuntu on old laptop and it worked well.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

I have only used gpt with new or reconfigured drives & larger flash drives since 2010. But with BIOS, you have to have a 1 or 2 MB unformatted partition with bios_grub flag for grub to correctly install. If I thought drive may be used with newer UEFI system later, I added both bios_grub & ESP. The only place to still use MBR is if you want Windows in BIOS boot mode. Windows will only boot in BIOS mode from MBR.

---

### Post by GhX6GZMB on 2021-05-23
2006...07 was exactly the time when Win Vista was around.

I suggest you do the following:
Power down and up again into the BIOS setup. Check for any settings to do with "Vista enhancements" or whatever and disable them. Also disable any "Fast boot" settings.

Save and power down, then boot with your live stick and when ready start the installer from the desktop.
When getting to the partitioning, select manual partitioning.
Make a partition with 25...30 GB, ext4, select "format", "mount point": / and tick the "boot" flag.
Make a partition with the rest of your space, ext4, select "format", "mount point": /home

This should get rid of remaining Vista gremlins.

Good Luck.

---

