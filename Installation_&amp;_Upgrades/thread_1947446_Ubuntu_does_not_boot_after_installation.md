---
title: "Ubuntu does not boot after installation"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by jruden on 2012-03-26
New motherboard (Asus P8H67) installing ubuntu 11.10 desktop i386.

Installation goes fine.

System does not boot after installation. I get sent to grub rescue prompt.

- The installation is done from a CD running in a SATA DVD-ROM.
- During installation my / disk is found and identified as sda.
- sda is an SSD which has been working fine until I got this new motherboard.
- Partition table on sda:
[INDENT][FONT="Courier New"]  sda1: / (ext4)
  sda2:   (swap)[/FONT][/INDENT]
- There are 2 other hard drives in the same box.

This is some I tried in grub rescue (typed in manually from a photo I took at it):

[FONT="Courier New"]grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1) (hd2) (hd2,msdos1)
grub rescue> set prefix=(hd0,0)/boot/grub
grub rescue> set root=(hd0,0)
grub rescue> insmod normal
error: no such partition.
grub rescue> set prefix=(hd1,0)/boot/grub
grub rescue> set root=(hd1,0)
grub rescue> insmod normal
error: no such partition.
grub rescue> set prefix=(hd2,0)/boot/grub
grub rescue> set root=(hd2,0)
grub rescue> insmod normal
error: no such partition.[/FONT]

Any clues what I should do? I have heard that there are some possible problems with the EFI bios on the Asus board but surely there must be some way to boot!? M$ has no problem booting in this box...

---

### Post by milkyky on 2012-03-26
what can i see u just have two partitions one is for /root one is for /swap right? i think u should have another partition name /boot right? 

Another question is did u have another external hard drive connected or just one SSD connected to your PC?

hope this can help.

---

### Post by jruden on 2012-03-27
> **milkyky said:**
> what can i see u just have two partitions one is for /root one is for /swap right? i think u should have another partition name /boot right? 

Another question is did u have another external hard drive connected or just one SSD connected to your PC?

hope this can help.
Thanks for the ideas. Normally you should be able to have only one partition on the whole disk if you want (/). Swap is optional (but often recommended). /boot can be on its own partition and traditionally it has been good to keep that early on the disk. In the case above I have partitioned the disk myself and did not let ubuntu do it - therefore it is like it is. I have however tried letting ubuntu installation handle the partitioning automatically and I get the same result then.

However I have found a thread now on this forum describing a possible solution to my problem. I will test this when I get a chance. They describe that in the case of these EFI motherboards you should create a FAT32 partition as first partition on the disk and create a folder /efi/grub on it. See this post (and its thread) [http://ubuntuforums.org/showpost.php?p=11549005&postcount=7](http://ubuntuforums.org/showpost.php?p=11549005&postcount=7)

I will investigate that solution and if it helps out my situation I will write so here.

---

### Post by darkod on 2012-03-27
Yes, I was just about to say that. In theory you could have only / on the whole disk but for EFI boot you need the EFI system partition to be the first on the disk.

Give it a shot and let us know.

Also note that if you plan to dual boot, there was some bug in grub2 and ubuntu and windows will "fight" for the EFI partition. The boot files for both systems should be on it, but during ubuntu install grub2 deletes the windows files. People have usually been able to copy them first and then just copy them back.

I have no EFI myself and can't test first hand.

---

### Post by oldfred on 2012-03-27
Your set root of 0,0 is using old grub notation. Grub2 starts at 1 so sda1 is (hd0,1).

UEFI only works with gpt partitioning. Windows will only boot in UEFI with gpt. But Windows usually installs to MBR and most drives are MBR. With MBR you do not have a efi partition.

With gpt you can use UEFI and a efi partition or in BIOS mode and gpt create a bios_grub.

So you have three choices. UEFI, gpt & efi partition, BIOS, gpt & bios_grub partition or the traditional BIOS & MBR partitioning. 

I only use gpt on all new drives but do not ever plan on having Windows on those drives. My XP is still MBR but I use it very little.

You may have some other settings in UEFI/BIOS that make a difference. Defaults are not always what works best.

---

### Post by jruden on 2012-04-01
Ok I have done some more testing now, but I still have no successful boot from the hard drive. I tried changing partition table on the drive to GPT instead of MSDOS. Then I created a fat32 partition as sda1 on it with a live cd and added the folder /efi/grub on is as mentioned in other thread. I also set the boot flag on that partition. I also created a / partition as sda2 and a swap as sda3. Installed 11.10 and installation, again, went fine, but only grub rescue on boot.

I tried then with 12.04 beta 2. I stopped the box and disconnected all other drives (leaving only the one I install ubuntu on). Left partition table as GPT and let ubuntu installation do the partitioning completely on its own.

No boot. Still only grub rescue.

Starting to get worried I will never see ubuntu run on my new box. :-(

---

### Post by oldfred on 2012-04-01
Are you booting in UEFI or BIOS.

If BIOS you need a small 1MB bios_grub partition. It can be anywhere on drive.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning.
You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS.

Post link to boot info script that this creates:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by jruden on 2012-04-01
> **oldfred said:**
> Are you booting in UEFI or BIOS.
Not completely sure. The Asus Motherboard's "bios application" offer for boot of USB attached devices both "UEFI Sandisk" and "Sandisk" (for instance). My SATA devices however are shown only as "Samsung ...." or "Corsair..." so I assume if it is using the same notation as for USB it is only BIOS boot(?)

> **oldfred said:**
> If BIOS you need a small 1MB bios_grub partition. It can be anywhere on drive.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning.
You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS.

Post link to boot info script that this creates:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.
My understanding is that I will try with GPT partition table and bios boot. I think the below summaries a possible setup:

[FONT="Courier New"]SDA: partition table type: GPT
 sda1: (1MB) type: EF02 flags: bios_grub
 sda2: (119 MB) type: linux flags: -[/FONT]

Question: Should sda1 also have boot flag?

Anything else?

---

### Post by oldfred on 2012-04-01
No flags should be required. Grub does not use a boot flag and in gpt there is no boot flag. Parted calls the efi partition a boot flag but it really is just a efi code as the bootable partition.

But a few Intel BIOS seemed to required a boot flag for both MBR & gpt, so if Intel you may have to add one even though it is not supposed to be used with BIOS and gpt.

---

### Post by jruden on 2012-04-01
I tried the following setup but it did not work. However the behaviour at boot was a bit different. Instead of giving the grub rescue prompt rather immediately it now was completely black (not even a visible cursor blinking). I thought it had crashed like so but after a rather long timeout minute(?) I was presented with a black/white ascii grub menu(!) However pressing the ubuntu boot alternative just resulted in grub prompt.

I used this setup:
[IMG]https://lh4.googleusercontent.com/-FRNi019UOBM/T3iwMQgau9I/AAAAAAAACTs/JfIRi8ASXbY/s640/IMAGE_2503BC18-9442-4350-8796-38C9A1B63707.JPG[/IMG]

Question1: Was it OK to use ext2 as file system time for grub_bios partition (sda1)?

Question2: Was it OK to store boot loader in sda? Or should it had been in sda1?

If no appearent errors with above config I shall test GPT partition...

---

### Post by oldfred on 2012-04-01
Bios_grub has no format.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

### Post by jruden on 2012-04-01
Nah, I am not getting this to work.
I have tried

- MSDOS partition table
- GPT partition table
- 500mb partition (fat16) with efi/grub folder
- 1mb unformatted partition with grub_bios flag on it

It just does not boot.

---

### Post by oldfred on 2012-04-01
Post link to boot info script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

