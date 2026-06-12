---
title: "FAIL: Migrating MBR to GPT on Intel dg965wh BIOS mb? Will not boot :("
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by cheryljosie on 2014-08-22
Solution is on [http://www.linuxquestions.org/questions/showthread.php?p=5225676#post5225676](http://www.linuxquestions.org/questions/showthread.php?p=5225676#post5225676)

Short story is I migrated a Core2 Duo BIOS boot file server from smaller 512B drives to larger 4KiB drives and aligned/converted to GPT using (probably) gdisk (cannot remember, it was a year ago).

Then I moved/resized all the partitions to fit using gparted, changed the VFAT boot partition (with GRUB to chainload the other OSs) to a bios-grub partition (no EFI on this motherboard) probably using gparted again, booted from a liveCD and chrooted to the existing 12.04 partition, and ran grub-install. I decided to forego chainloading since I do not know how to do it with grub2 and I doubt grub will boot a BIOS system on GPT without EFI. So I just let the existing main OS install grub2 on the bios-grub partition.

The grub-install seemed to work fine but when I restarted the BIOS says insert bootable media or something like that. It is not finding the bootloader.

Several potential issues include:

Is there a protective MBR on the GPT drive? Did I pass the correct parameter to gdisk? How can I find out? I do not remember what I did.

Does Ubuntu installed on MBR have the required libraries and configuration files to grub-install to a GPT? How do I find out/fix? this usually occurs during hardware discovery in a full installation.

Some motherboards cannot boot GPT, or require some special configuration to do it. How do I find out if this one is compatible? Intel dg965wh
After resizing and moving partitions, the 200MB bios-grub partition is the first one at the very beginning but it is not number 0. Does that matter?

Several forums indicate setting a boot flag but it must be done in the protective MBR and only one tool can do it? I tried and it did not help. Not only that, I could not verify I did it correctly because each tool handles the reporting differently and I do not know how to check if it matters or is done right.

I would start over but there are two main reasons I prefer not to. First, I might have done nothing at all wrong, it might be the motherboard or Linux. Second, the MythTV installation needs the exact same OS or I have to back up the entire MySQL database and it is a risky process. Third, I already went through all the trouble of repartitioning. Fourth, I already tried installing from liveCD to a small ATA drive but it will not let me install to a GPT so I cannot test it that way. Fifth, I do not want to reformat the original copy since it is my backup and the drives are only SATA 1.5TB and I do not know if the Ubuntu install will even let me put a GPT on them since MBR works up to 2TB and the install from liveCD would not let me do it on a small ATA. So here I am with no easy way to confirm if my MB is compatible with GPT bios booting or not. Another drive is too expensive to contemplate at this time.

Any suggestions? Stuck troubleshooting this for a full year. Many thanks for your patience.

---

### Post by oldfred on 2014-08-24
I have been booting Ubuntu from a gpt partitioned drive since version 10.10 with BIOS. I have even converted my full install of Ubuntu on my 16GB flash drive to use gpt partitioning.
It is a dual core Intel based system with a nVidia card.
My motherboard is a Gigabyte EP43-UD3L.

You do have to have a bios_grub partition for grub to correctly install to the protective MBR.
 In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

Many Intel motherboard require a boot flag on a partition. Grub does not use a boot flag, that is required by Windows with BIOS boot for Windows to know which primary partition has more boot files.

We have also seen Intel motherboard require a boot flag on a partition with even gpt partitioning booting in BIOS mode. But with gpt the only partition that is supposed to have a boot flag is the efi partition.
If drive would never be copied to a UEFI system, I might create a tiny efi partition and add boot flag. But boot in BIOS mode. If drive might be moved to a newer system create an efi partition of 300MB preferably near beginning of drive.

 Add boot flag (even though not required with gpt) - see post by srs5694
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)
Gparted did not add flag correctly but converted partition to efi?
[http://ubuntuforums.org/showthread.php?t=1686929](http://ubuntuforums.org/showthread.php?t=1686929)

---

