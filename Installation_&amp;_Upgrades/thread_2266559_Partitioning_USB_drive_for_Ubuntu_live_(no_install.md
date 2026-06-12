---
title: "Partitioning USB drive for Ubuntu live (no installation) and storage space"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by edward26 on 2015-02-23
Hello everyone!  First of all, I'm sorry if this question has already been answered by I looked through some of the previous posts and couldn't find an answer.  Also have spent about six hours trying to get this to work.

The scenario is this: I want to have my 32GB flash drive partitioned in such a way that 2GB are allocated for the ubuntu-14.04.2-desktop-amd64.iso image and the remaining 30GB are formatted as separate storage space.

I'm using a Mac and partition the drive via Disk Utility using GPT as its format.  I then create both partitions using Mac OS Extended (Journaled).  Using "diskutil list" I see my flash drive is "/dev/disk6".  I'm not exactly an expert at using this utilities so I assume there may be something wrong when using "dd" and "fdisk".  The command I use for dd is:

sudo dd if=/path/to/ubuntu.iso of=/dev/rdisk6s2 bs=1M

where I'm telling it to use "rdisk6s2" as the location of the ISO.  Is this correct?

So, I let this complete but then when I try to boot it, nothing happens.  So, I read that I need to set the boot flag using fdisk.  Here's the part that confuses me.  I run fdisk and select the rdisk6s2 partition and use "flag 2" because it appears that the large amount of data is there.  However, how does the computer know to look in rdisk6s2 and not in the first partition?

If anyone could please provide step-by-step instructions on how to accomplish this task, I would be greatly appreciative.  As it stands, I'm currently carrying a 64GB SDXC card as additional storage but it'd be nice if I could just use the 32GB flash drive as the Ubuntu ISO is about 1GB.

Thanks in advance!

---

### Post by oldfred on 2015-02-23
You are mixing a variety of formats.
Gpt is standard with UEFI, but installers use msdos with one FAT32 partition.

A ISO image was originally for CD or DVD, but flash drive installers extract it and add a boot loader for BIOS boot. But they use FAT32 and syslinux boot loader which works like Windows and needs boot flag. But if booting in UEFI mode the boot loader in the MBR is not used.
But a dd copy is an image created that does not use standard partitions, but is still bootable. It is not a standard partition neither gpt nor MBR but a hybrid iso9660 file system.

If booting with UEFI, you can just extract ISO to a partition. If gpt it must be FAT32 with the boot flag.

But you can also create grub bootable flash drives with many ISO (not extracted) and use grub2's loopmount feature to boot those ISO. Not all ISO work, but many installers do. That then needs grub installed to an efi partition on a gpt partitioned drive.

---

