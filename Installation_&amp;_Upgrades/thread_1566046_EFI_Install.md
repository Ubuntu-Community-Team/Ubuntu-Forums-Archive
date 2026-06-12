---
title: "EFI Install"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by X5-655 on 2010-09-01
Just whiped out my HD..  I hope I did this right, cause my Compaq laptop has EFI (I was using an EFI loader and had numerous problems with power management)..

Format HD as GPT.  Create 200MB FAT32 partition at begining of drive, mark it as EFI System Partition, have Ubuntu installer use largest free space, and install bootloader to SDA1 (the FAT32 partition).

it's installing right now..  I hope that works, I tried searching on how-to's that is NOT an intel mac, but found nothing..

---

### Post by X5-655 on 2010-09-01
nope didn't work..  upon boot it couldn't find a bootable device..

---

### Post by naelq on 2010-09-01
wow!! i've just found your thread regarding booting EFI (which was posted about an hour ago :p)
take a look at this: [http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/itanium-install-guide/s1-ia64-intro-efi-shell.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/itanium-install-guide/s1-ia64-intro-efi-shell.html) ;)

btw, & in case you wonder, i have a macbook (with EFI) which i use rEFIt & grub..
the reason i was looking for info regarding EFI is that i want to use it with my new XEON setup. why? simply because the MoBo (S3420GPLC) supports it :)

please update your progress, & i will update with mine, but 1st i have some backups to do..

Nael

---

### Post by X5-655 on 2010-09-01
I actually after countless attempts, found that HP disabled unsigned EFI code on the Compaq cause they aren't the EliteBook..  But I can use GPT atleast without problem, which is good, but sucks an EFI loader won't work..

There seems there may be a trick for me though, put grub2.efi in the HP_TOOLS partition, which is the EFI partition on this laptop..

---

### Post by oldfred on 2010-09-02
Grub2 seems to be just now making improvements in using efi to boot.

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
OP installs gpt with gdisk
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)

---

### Post by X5-655 on 2010-09-02
I actually setup a GPT disk with both GParted and Gnome Disk Utility..  It works, but my laptops EFI is denying GRUB2, "Unsigned"..  It sees it, it puts grub2.efi in HP_TOOLS which is a marked EFI System Partition at the begining of the disk, but in the end it seems to boot to this odd partition:  [http://img.photobucket.com/albums/v395/Evilweredragon/oddpartition.png](http://img.photobucket.com/albums/v395/Evilweredragon/oddpartition.png)

---

### Post by oldfred on 2010-09-02
My gpt install on sdb looks like yours (but without boot partition as I only have MBR BIOS.

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

It seems that many tools are not totally updated for gpt so they just show unknown.

I do not know if you can have the bios_grub partition be the efi boot partition or not. The efi partition is the one that the efi boot loader will use for booting , but I do not know if you can let grub put its files in that also.

---

### Post by oldfred on 2010-09-02
Since you have space in your Ubuntu install, I would shrink it by 20-25GB for another ext4 partition and just install the latest Maverick. They just came out with a new beta today, so it may be worth testing.

---

### Post by srs5694 on 2010-09-02
> **oldfred said:**
> [http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown

It seems that many tools are not totally updated for gpt so they just show unknown.

GNU Parted, GParted, and similar tools look inside partitions to identify the filesystems they contain. A BIOS Boot Partition, however, contains no filesystem; it contains raw boot code used by GRUB 2. (At least, this is true once GRUB 2 is fully installed; you can of course put a filesystem on the partition, but this will break GRUB 2 if it's already been installed, and if you re-install GRUB 2, doing so will destroy the filesystem.) Thus, the identification of a BIOS Boot Partition as "unknown" has nothing to do with the fact that the disk is GPT, except insofar as a BIOS Boot Partition is a GPT partition type with no exact MBR equivalent. Rather, it has to do with the fact that libparted doesn't (yet?) know how to identify the GRUB 2 boot code that goes in the BIOS Boot Partition. GNU Parted *does* identify the partition's type by reporting it as having the "bios_grub flag" set.

> I do not know if you can have the bios_grub partition be the efi boot partition or not. The efi partition is the one that the efi boot loader will use for booting , but I do not know if you can let grub put its files in that also.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used *without a filesystem* for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI *with a FAT-32 filesystem* for storing EFI files, the two *cannot* be the same partition. What's more, GNU Parted's method of identifying these partitions (with "flags") obscures the fact that they have different partition type codes. Each partition can have just one type code ("flag" in GNU Parted parlance), so a partition may be flagged as being of one of these types at most. (There are other type codes, too, of course -- see the "Partition Type GUIDs" table on the [Wikipedia entry for GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) for details.

The BIOS Boot Partition is used by GRUB 2 on BIOS-based systems. I have no idea if GRUB 2 requires this partition on EFI-based systems. Creating such a partition will do no harm, so if you're installing on an EFI-based system, you might as well create this partition.

---

### Post by Skaperen on 2010-09-02
I find parted an ugly program that sometimes does very comical things.  I have found a program called gdisk that works better because it works just like fdisk which I am already familiar with.  I'll be using gdisk until I finally get around to writing my own partitioning utility.

---

### Post by oldfred on 2010-09-02
Skaperen, I am sure srs5694 appreciates the recommendation on gdisk as he is the author. :)

I now see gdisk is in the repository (synaptic) so it is easy to download.

---

### Post by X5-655 on 2010-09-02
The "HP_TOOLS" is my laptops EFI partition..  It's the only EFI partition it will recognize and must be named HP_TOOLS.  If I rename it, I can't even go into BIOS setup..

But I did put grub2.efi in there, and try to load it, but the laptop doesn't want to execute it..  If I put this HD in an EliteBook, it DOES load the EFI Grub loader..

So something tells me HP crippled the EFI in my Compaq laptop, to only load HP EFI pre-boot apps, and not non-HP apps..

In HP's EFI handbook, it says in EFI setup, there's an option for "Allow Boot from EFI File" or something like that, mine don't have it, it's hidden..

So maybe that's why GRUB made a 1MB partition on the GPT disk, because it can't put anything in the EFI partition, and there is no MBR on this disk.

---

### Post by srs5694 on 2010-09-02
> **oldfred said:**
> I now see gdisk is in the repository (synaptic) so it is easy to download.

One caveat: The gdisk version in the Ubuntu repository is a bit elderly -- it's 0.5.1 (released November 30, 2009), but the latest version is 0.6.10 (released August 22, 2010). 0.5.1 has a number of bugs; see the [revisions page](http://www.rodsbooks.com/gdisk/revisions.html) of the gdisk documentation for details. I therefore recommend downloading and installing the Debian package for your architecture from the [Sourceforge project page.](https://sourceforge.net/projects/gptfdisk/files/) I've tested both the i386 and amd64 packages on Ubuntu.

[quote=X5-655]So maybe that's why GRUB made a 1MB partition on the GPT disk, because it can't put anything in the EFI partition, and there is no MBR on this disk. [/quote]

AFAIK, GRUB can't modify the partition table. The Ubuntu installer can create partitions. I don't know offhand what sort of logic it uses for what types of partitions to create on GPT disks. As a general rule, BIOS-based systems need a BIOS Boot Partition but not an EFI System Partition, whereas EFI-based systems need an ESP System Partition. (I'm not sure offhand if GRUB 2 needs a BIOS Boot Partition even on EFI-based systems, but my guess would be not.)

---

### Post by X5-655 on 2010-09-02
Ok well here's how I partitioned it..

Format drive as GPT with Gnome Disk Utility, create 200MB FAT32 with GParted (because I couldn't get Gnome Disk Utility to make a FAT32 partition, only FAT16), and flag it as an EFI System Partition with Gnome Disk Utility..  I then name the partition "HP_TOOLS" (this is what HP requires their EFI partition to be named), and put my HP EFI stuff on it, bios.efi, systemdiags.efi, etc...

I then load Ubuntu installer, and tell it to use the largest free space, and that is what I was left with, what is seen in the screenshot..

If I go into synaptic and switch it to Grub-efi AMD64, it never puts grub2.efi in the EFI partition, and the laptop ends up booting to the grub BIOS partition..

I tried to download a copy of grub2.efi (i know, a poor way to do it, but was a test), and stuck it in the EFI partition..  No dice, my laptops EFI ignored it..  So I renamed HP's SystemDiags.efi to SystemDiags.bak, and renamed Grub2.efi to SystemDiags.efi, and upon boot, I told the laptop to go into it's System Diagnostics utility, and I get something about non hp signed preboot not allowed..

I'm contacting HP about this right now, because this laptop is advertised with EFI, but it seems HP only allows the Compaqs to only run the HP EFI utilities, and that's it..  HP Elite Books in the boot menu allow you to enter the path to an EFI file, but mine doesn't..  (yet the menu otherwise looks the same)..

---

### Post by oldfred on 2010-09-02
Are you running the latest version of the efi loader, like a BIOS update?

The manual says you can run unsigned but they of course do not recommend it.

If you want to launch non–HP-signed EFI applications for development purposes, follow these steps:
1. Access the Computer Setup utility and select System Configuration.
2. Select Device Configurations, select UEFI Boot Mode, and then select Enabled.

---

### Post by X5-655 on 2010-09-02
> **oldfred said:**
> Are you running the latest version of the efi loader, like a BIOS update?

The manual says you can run unsigned but they of course do not recommend it.

If you want to launch non–HP-signed EFI applications for development purposes, follow these steps:
1. Access the Computer Setup utility and select System Configuration.
2. Select Device Configurations, select UEFI Boot Mode, and then select Enabled.

Here's the problem, HP left out "UEFI Boot Mode" out of my system configure page in the setup utility..  That's why I also contacted HP via email, and hope for a response soon..  They just didn't put that important control in my setup utility..

---

### Post by X5-655 on 2010-09-02
See here, it's missing that crucial option in the EFI Setup.

[http://img.photobucket.com/albums/v395/Evilweredragon/efi1-1.jpg](http://img.photobucket.com/albums/v395/Evilweredragon/efi1-1.jpg)

(Boot options is just a boot order page, net boot, USB boot, etc, but nothing relating to EFI either).

The EFI partition houses this:
[http://img.photobucket.com/albums/v395/Evilweredragon/efi2-1.jpg](http://img.photobucket.com/albums/v395/Evilweredragon/efi2-1.jpg)
[http://img.photobucket.com/albums/v395/Evilweredragon/efi3.jpg](http://img.photobucket.com/albums/v395/Evilweredragon/efi3.jpg)

---

### Post by Funckyfizz on 2011-10-17
I think this problem has been solved in the thread posted earlyer ([http://ubuntuforums.org/showthread.php?t=1563699&page=5](http://ubuntuforums.org/showthread.php?t=1563699&page=5)) the last post indecates that 11.04 installs with UEFI automatically and works well. Hopefully this will work better than the BIOS version since (unix based) OSX uses EFI. Although I do not have enough knowledge to say if it will.

---

