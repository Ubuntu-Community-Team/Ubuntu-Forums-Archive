---
title: "Why does Ubuntu limit me to 4 partitions"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by TheGuvernor on 2011-08-10
when they support GPT in Grub2? Am I correct that the 4 partition limit was only a limit in MBR? Is there something special I need to do to enable this?

I'm aware of logical partitions but I'm just curious about the above.

---

### Post by haqking on 2011-08-10
> **TheGuvernor said:**
> when they support GPT in Grub2? Am I correct that the 4 partition limit was only a limit in MBR? Is there something special I need to do to enable this?

I'm aware of logical partitions but I'm just curious about the above.

Ubuntu isnt limiting you.

it is 4 primary partitions, you can create 3 and a logical with logicals as you like.

why do you want more than 4 primaries ?

and linux does support GPT, and yes the limit is due to MBR.

---

### Post by srs5694 on 2011-08-10
If you feed the Ubuntu installer a completely blank disk, with no partition table on it, the installer creates an MBR partition table on disks smaller than 1 TB. Somewhere between 1 TB and 2 TB (I'm not sure of the exact value), the installer switches to using GPT on blank disks. You can also force the installer to use either MBR or GPT by creating a partition table on the disk before you launch the installer.

If you're installing to a GPT disk on a BIOS-based computer, be sure to create a [BIOS Boot Partition.](http://en.wikipedia.org/wiki/BIOS_Boot_partition) This partition holds about 30 KB of GRUB code, and although GRUB can theoretically work without it, sometimes it refuses to install or will misbehave once installed if the BIOS Boot Partition isn't present. There are also rare [BIOS quirks with GPT.](http://nessus.rodsbooks.com/gdisk/bios.html) These seem to be most common on Intel-branded motherboards. Fortunately, they're easy to work around if you understand them, but they're very frustrating if you don't.

---

### Post by TheGuvernor on 2011-08-10
> **srs5694 said:**
> If you feed the Ubuntu installer a completely blank disk, with no partition table on it, the installer creates an MBR partition table on disks smaller than 1 TB. Somewhere between 1 TB and 2 TB (I'm not sure of the exact value), the installer switches to using GPT on blank disks. You can also force the installer to use either MBR or GPT by creating a partition table on the disk before you launch the installer.

If you're installing to a GPT disk on a BIOS-based computer, be sure to create a [BIOS Boot Partition.](http://en.wikipedia.org/wiki/BIOS_Boot_partition) This partition holds about 30 KB of GRUB code, and although GRUB can theoretically work without it, sometimes it refuses to install or will misbehave once installed if the BIOS Boot Partition isn't present. There are also rare [BIOS quirks with GPT.](http://nessus.rodsbooks.com/gdisk/bios.html) These seem to be most common on Intel-branded motherboards. Fortunately, they're easy to work around if you understand them, but they're very frustrating if you don't.

Thank you! The disk size has got to be it. I have a new 500 gig disk. I'll give a try to forcing it tonight.

---

### Post by Luke M on 2011-08-10
Grub can boot from logical partitions, so I don't understand what the issue is.

---

### Post by TheGuvernor on 2011-08-10
> **haqking said:**
> Ubuntu isnt limiting you.
Not sure what else it would be then? Please see above. My disk is a 500 gig disk.

> it is 4 primary partitions, you can create 3 and a logical with logicals as you like.
I know. Please see above

> why do you want more than 4 primaries ?
For stuff like FreeBSD (and other things) which require a primary

---

### Post by TheGuvernor on 2011-08-10
> **Luke M said:**
> Grub can boot from logical partitions, so I don't understand what the issue is.

For stuff like FreeBSD (and other things) which require a primary

---

### Post by oldfred on 2011-08-10
srs5694 sold me on gpt. Since my old XP is on a separate MBR drive I do not have to worry. So I formated my 160GB drive to gpt, created the bios_grub, & / (root) partitions in advance and it just worked.

I also used gpt on a 16GB flash drive and it worked there also. I did this before gparted & gdisk changed to use better rounding, it should start at sector 40 and all other sectors startshould be divisible by 8.

```
fred@fred-MavericDT:~$ sudo parted /dev/sdb unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s                                bios_grub
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4

```

---

### Post by YesWeCan on 2011-08-10
@oldfred
What is Maverick using to recognize the partitions on the disk - the GPT or the MBR PT? Eg: if you run sudo fdisk -l what entries does it show in the MBR PT?

[edit]That's a silly question. I am just interested in the contents of the MBR PT which should have a "protective" entry.

Grub will have put boot code in the MBR area that boots another boot code in the bios_grub partition, that loads and runs the Grub kernel. The Grub kernel then gets the rest of its files from the Maverick boot partition as usual.

As an aside, being able to make a bios_grub partition on an MBR disk would be very, very useful for same-disk dual booting with Windows but as I understand it this is not allowed. I am not sure why it is not allowed.

---

### Post by oldfred on 2011-08-10
I have BIOS and it has the protective MBR.

boot script shows this:

```
Drive: sdb __________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34        16,064        16,031 BIOS Boot partition
/dev/sdb2          16,065    51,215,219    51,199,155 Data partition (Windows/Linux)
/dev/sdb3      51,215,220    57,352,049     6,136,830 Swap partition (Linux)
/dev/sdb4      57,352,050   312,576,704   255,224,655 Data partition (Windows/Linux)
```But my standard fdsik does not which confuses me as it should and I thought it used to, but I may only be remembering boot script:

```
Disk /dev/sdb: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312576705 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              34       16064        8001   83  Linux 
/dev/sdb2           16065    51215219    25591545   83  Linux 
/dev/sdb3        51215220    57352049     3060382   82  Linux Swap / Solaris 
/dev/sdb4        57352050   312576704   127604295   83  Linux 

```sfdisk:
```
fred@fred-MavericDT:~$ sudo sfdisk -d /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.

# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=        1, size=312581807, Id=ee
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
fred@fred-MavericDT:~$
```

---

### Post by TheGuvernor on 2011-08-10
@oldfred

Why does your swap say Solaris? Are you using the same swap partition for both?

---

### Post by YesWeCan on 2011-08-10
Thanks oldfred. At least sfdisk tells you that there is a GPT present. Perhaps best to use sudo parted -l.

---

### Post by oldfred on 2011-08-10
Just for completeness sudo parted l shows it is gpt partition table:

```
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  8225kB  8208kB                            bios_grub
 2      8225kB  26.2GB  26.2GB  ext4            MAVERICK
 3      26.2GB  29.4GB  3142MB  linux-swap(v1)
 4      29.4GB  160GB   131GB   ext4

```I am not running solaris, I think the partition type code just translates to text the same.

fred@fred-MavericDT:~$ sudo sfdisk -T
Id  Name
...
82  Linux swap / Solaris
83  Linux
84  OS/2 hidden C: drive

---

### Post by dFlyer on 2011-08-10
You can only have 4 primary partitions regardless if it's windows or linux. You can have all the logical partitions you want. As stated above linux can boot logical partitions.

---

### Post by TheGuvernor on 2011-08-10
> **dFlyer said:**
> You can only have 4 primary partitions regardless if it's windows or linux. You can have all the logical partitions you want. As stated above linux can boot logical partitions.

You can have more than 4 primaries with GPT. You can only have 4 with MBR

---

### Post by YesWeCan on 2011-08-10
It seems to me the main benefit (not the only one) of GPT is that it can be used to reliably partition disks bigger than 2TB.
Back in Fred Flinstone's era when the IBM MBR was designed, I imagine a big disk was probably 10MB or something.
Both the MBR and GPT can have a huge number of partitions and from linux's perspective it doesn't matter whether they are primary or logical. Windows prefers primaries, tho.

---

### Post by TheGuvernor on 2011-08-10
> **YesWeCan said:**
> It seems to me the main benefit (not the only one) of GPT is that it can be used to reliably partition disks bigger than 2TB.
Back in Fred Flinstone's era when the IBM MBR was designed, I imagine a big disk was probably 10MB or something.
Both the MBR and GPT can have a huge number of partitions and from linux's perspective it doesn't matter whether they are primary or logical. Windows prefers primaries, tho.

Someone who is more knowledgable than me may want to chime in here but my understanding is that is the case (you're correct) if you're using it with BIOS. However if you're using it with UEFI (which is often referred to as BIOS but isn't) you also get the additional benefits of:

Faster boot-up
CPU-independent architecture
CPU-independent drivers
Flexible pre-OS environment, including network capability
Modular design

Wiki on UEFI is here for anyone interested [http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

P.S. I forgot:

Encryption
Network Auth
UX

---

### Post by YesWeCan on 2011-08-10
I guess the question is how many of those UEFI benefits depend on GPT as opposed to being implemented only on GPT? In principle one could create an EFI boot partition on an MBR PT disk, for example. But it is a non-point as things are how they are given to us.

---

### Post by srs5694 on 2011-08-10
> **TheGuvernor said:**
> [quote=haqking]why do you want more than 4 primaries ? 			 		
For stuff like FreeBSD (and other things) which require a primary[/QUOTE]

The last I checked, FreeBSD's normal installation on an MBR disk requires *one* primary partition, which it then carves up into multiple sub-partitions. This is conceptually similar to an extended partition that houses logical partitions, although of course the implementation details differ. (Of course, if you want to install multiple BSDs you might run out of primaries.)

Also, the last I checked (a few months ago), the FreeBSD installer couldn't install directly to GPT, so to use GPT with FreeBSD, you've got to install in a somewhat roundabout manner. I recently installed [PC-BSD](http://www.pcbsd.org/) in a virtual machine, and it has a GPT installation option, so either it's a bit ahead of FreeBSD in this respect or my knowledge of FreeBSD is a bit behind the times. I recommend you research this detail before diving in too deeply.

> **oldfred]I have BIOS and it has the protective MBR.

boot script shows this:

 	Code:
 	Drive: sdb __________________________________
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34        16,064        16,031 BIOS Boot partition
/dev/sdb2          16,065    51,215,219    51,199,155 Data partition (Windows/Linux)
/dev/sdb3      51,215,220    57,352,049     6,136,830 Swap partition (Linux)
/dev/sdb4      57,352,050   312,576,704   255,224,655 Data partition (Windows/Linux) 
But my standard fdsik does not which confuses me as it should and I  thought it used to, but I may only be remembering boot script:

 	Code:
 	Disk /dev/sdb: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312576705 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              34       16064        8001   83  Linux 
/dev/sdb2           16065    51215219    25591545   83  Linux 
/dev/sdb3        51215220    57352049     3060382   82  Linux Swap / Solaris 
/dev/sdb4        57352050   312576704   127604295   83  Linux 
[/quote]

My suspicion is that you've installed GNU fdisk, which is designed to mimic Linux's fdisk said:**
> Why does your swap say Solaris? Are you using the same swap partition for both?

In MBR, the type code for Linux swap space is the same as an old type code for Solaris filesystem data. Thus, Linux fdisk reports it as "Linux swap / Solaris", since it could be either. If my hypothesis about oldfred having GNU fdisk installed is correct, then GNU fdisk is just mimicking Linux fdisk's behavior on this score, even on GPT disks, on which this type code collision doesn't exist.

> **YesWeCan]It seems to me the main benefit (not the only one) of GPT is that it can be used to reliably partition disks bigger than 2TB.[/quote]

Correct, although MBR's limit is 2 tebibytes (TiB), not 2 terabytes (TB). (That's a 10% difference.)

Other advantages of GPT include:


[list]
[*]GPT makes no distinction between primary, extended, and logical partitions. (Technically, "primary partition" is an MBR concept that doesn't even apply in GPT said:**
> A backup of important partition table data exists at the end of the disk, which can help in recovery if the main partition table is accidentally overwritten.
[*]Checksums of important GPT data are stored on disk, which can help OSes and utilities identify corrupted data structures. Theoretically, this can improve reliability.
[*]Partitions can be given names, which can help you identify the purpose of partitions. (Of course, filesystem names can do the same even on MBR disks, but not all tools show you filesystem names.)
[*]Partition type codes are 16-byte GUID values, as opposed to 1-byte values for MBR partition type codes. This makes type code collisions unnecessary, although one important one already exists: Linux commonly uses the same type code as Windows for its data partitions. (This is likely to change soon, though; a new Linux-specific filesystem type code has been defined, although it's not yet widely implemented.)
[*]Cylinder/head/sector (CHS) geometries aren't used, except in a minor role in the "protective MBR" (which exists to keep GPT-unaware tools from messing with the GPT disk). In MBR, by contrast, partitions are described in both logical block addressing (LBA) and CHS terms, which can lead to inconsistencies, at least on partitions below approximately 8 MB (where CHS maxes out).
[/list]


[quote=TheGuvernor]Someone who is more knowledgable than me may want to chime in here but  my understanding is that is the case (you're correct) if you're using it  with BIOS. However if you're using it with UEFI (which is often  referred to as BIOS but isn't) you also get the additional benefits of:

Faster boot-up
CPU-independent architecture
CPU-independent drivers
Flexible pre-OS environment, including network capability
Modular design
...
Encryption
Network Auth
UX

[quote=YesWeCan]I guess the question is how many of those UEFI benefits depend on GPT as  opposed to being implemented only on GPT? In principle one could create  an EFI boot partition on an MBR PT disk, for example. But it is a  non-point as things are how they are given to us.[/quote]

AFAIK, none of the UEFI advantages that TheGuvernor has noted derive from GPT per se. UEFI can handle both MBR and GPT, and in principle an implementation could handle other partition types, too. (Apple's EFI can boot from APM, for example.)

There's an MBR type code for an EFI System Partition (ESP); it's type code 0xEF. I don't think I've ever tried it, but you should be able to boot Linux from an MBR disk on a UEFI-based system using EFI boot mode by creating such a partition and putting the appropriate boot loader files on it.

Windows, however, ties partition table types to firmware types quite rigidly for its boot disks; under Windows, if you use BIOS boot mode, your boot disk *must* be MBR, and if you use UEFI boot mode, your boot disk *must* be GPT.

---

### Post by TheGuvernor on 2011-08-11
> **srs5694 said:**
> I recently installed [PC-BSD](http://www.pcbsd.org/) in a virtual machine, and it has a GPT installation option, so either it's a bit ahead of FreeBSD in this respect or my knowledge of FreeBSD is a bit behind the times. I recommend you research this detail before diving in too deeply.

Were you using VMWare, VirtualBox or something else?

---

### Post by srs5694 on 2011-08-11
> **TheGuvernor said:**
> [quote=srs5694]I recently installed [PC-BSD]("http://www.pcbsd.org/")  in a virtual machineWere you using VMWare, VirtualBox or something else?[/QUOTE]

I used VirtualBox.

---

### Post by TheGuvernor on 2011-08-11
> **srs5694 said:**
> My suspicion is that you've installed GNU fdisk, which is designed to mimic Linux's fdisk; however, GNU fdisk is based on libparted and therefore understands GPT and shows you the GPT partitions as if they were MBR partitions. IMHO, it's best to remove GNU fdisk and (if necessary) re-install Linux's standard fdisk (from the util-linux package in Ubuntu). The reason is that Linux fdisk uses a different code base than does libparted (and hence GNU fdisk, parted, GParted, etc.). Using nothing but libparted-based tools ties you to libparted's strengths and weaknesses for everything, whereas having two different code sets available gives you more options for working around problems and obtaining diagnostic information.

Sorry to keep bugging you but you seem to be one of the most knowledgeable Linux people I've ever seen :P


I was researching the above after reading what you wrote and dug through my /sbin. I have cfdisk. How does this differ from fdisk? Is it like GNU fdisk or just like fdisk? From what I gather it was dev'd by RH and is more graphical but I couldn't really find the answer to my other question which is based upon your post.

---

### Post by srs5694 on 2011-08-11
There are three disk partitioning tools included in the util-linux package:


[list]
[*]**fdisk** -- This is the "basic" program. It has an interactive text-mode interface that scrolls by on the screen, so you could capture its output and read through it and see what's been done.
[*]**sfdisk** -- This program is intended for use in scripts, from the command line (as in, type a single command to have the program do something), and to create or modify partition tables based on stored files. It's not very newbie-friendly, but it's the quickest way to accomplish certain tasks, such as recording a backup of all the partitions on the disk.
[*]**cfdisk** -- This program features an interactive text-mode interface that uses the curses interface (hence the "c" in "cfdisk"). The curses interface enables programs to move the cursor around, clear the screen, etc. It's often used by text editors, and cfdisk provides a similar dynamic interface. Some people find this easier to use than fdisk, but because of the dynamic nature of the display, you can't just scroll back to see what's recently been done. It's also got fewer options than fdisk.
[/list]


GNU fdisk was designed to work just like Linux fdisk, but to be based on libparted. There are areas where GNU fdisk's emulation of Linux fdisk doesn't quite work right, and libparted has its own quirks -- and some advantages, like its ability to handle GPT. OTOH, my GPT fdisk (gdisk) gives much better access to GPT's features than does libparted, IMHO, with an fdisk-like interface.

---

### Post by YesWeCan on 2011-08-12
> **srs5694 said:**
> 
Correct, although MBR's limit is 2 tebibytes (TiB), not 2 terabytes (TB). (That's a 10% difference.)
Very true, but I feel the need to "out-pedant" you. :P More accurately, MBR is limited to a 4 byte representation of block addresses, so it will vary depending on the block size for a disk.

> Other advantages of GPT include:


[LIST]
[*]GPT makes no distinction between primary, extended, and logical partitions. (Technically, "primary partition" is an MBR concept that doesn't even apply in GPT; in GPT, all partitions are just "partitions.")
[*]A backup of important partition table data exists at the end of the disk, which can help in recovery if the main partition table is accidentally overwritten.
[*]Checksums of important GPT data are stored on disk, which can help OSes and utilities identify corrupted data structures. Theoretically, this can improve reliability.
[*]Partitions can be given names, which can help you identify the purpose of partitions. (Of course, filesystem names can do the same even on MBR disks, but not all tools show you filesystem names.)
[*]Partition type codes are 16-byte GUID values, as opposed to 1-byte values for MBR partition type codes. This makes type code collisions unnecessary, although one important one already exists: Linux commonly uses the same type code as Windows for its data partitions. (This is likely to change soon, though; a new Linux-specific filesystem type code has been defined, although it's not yet widely implemented.)
[*]Cylinder/head/sector (CHS) geometries aren't used, except in a minor role in the "protective MBR" (which exists to keep GPT-unaware tools from messing with the GPT disk). In MBR, by contrast, partitions are described in both logical block addressing (LBA) and CHS terms, which can lead to inconsistencies, at least on partitions below approximately 8 MB (where CHS maxes out).
[/LIST]
Handy summary. 

> AFAIK, none of the UEFI advantages that TheGuvernor has noted derive from GPT per se. UEFI can handle both MBR and GPT, and in principle an implementation could handle other partition types, too. (Apple's EFI can boot from APM, for example.)

There's an MBR type code for an EFI System Partition (ESP); it's type code 0xEF. I don't think I've ever tried it, but you should be able to boot Linux from an MBR disk on a UEFI-based system using EFI boot mode by creating such a partition and putting the appropriate boot loader files on it.

Windows, however, ties partition table types to firmware types quite rigidly for its boot disks; under Windows, if you use BIOS boot mode, your boot disk *must* be MBR, and if you use UEFI boot mode, your boot disk *must* be GPT.Understood.


Just out of interest. Is it the intention of UEFI that the choice of OS to boot is made in the bios stage rather than by a bespoke EFI boot loader program? IOW is the "Unified" aspect of Grub becoming redundant? Should Canonical make a special, simple, reliable EFI boot loader that just boots the Ubuntu OS that installed it?

Suppose GPT has 4 separate Ubuntu installations and an EFI System Partition. Is the intentention that there are 4 separate .efi files that can be chosen from the UEFI bios menu? Or is this not clear at this stage?

And what happens when there are multiple disks and more than one ESP? Does the bios UEFI concatenate their contents into one single menu selection?

---

### Post by srs5694 on 2011-08-12
> **YesWeCan said:**
> Very true, but I feel the need to "out-pedant" you. :P More accurately, MBR is limited to a 4 byte representation of block addresses, so it will vary depending on the block size for a disk.

True. The industry is moving toward a 4096-byte sector size, which will raise the limit from 2 TiB to 16 TiB. At the moment, although disks with 4096-byte physical sectors exist, AFAIK they all present the illusion of having 512-byte sectors, so for them, a 32-bit pointer still works out to 2 TiB. A few external disks and, if I'm not mistaken, RAID controllers, present the illusion of larger-than-512-byte sector sizes, either by default or as configuration options.

> Just out of interest. Is it the intention of UEFI that the choice of OS to boot is made in the bios stage rather than by a bespoke EFI boot loader program? IOW is the "Unified" aspect of Grub becoming redundant? Should Canonical make a special, simple, reliable EFI boot loader that just boots the Ubuntu OS that installed it?

I can't speak to the intent of the EFI and UEFI developers, since I don't recall the intent being laid out in the standards documents (which can be obtained from the [UEFI specifications](http://www.uefi.org/specs/) page, although you've got to click a couple of links and agree to the terms and conditions).

In theory, the firmware of an EFI or UEFI computer can be used to select the OS to boot. In practice, most (U)EFI implementations make this more difficult than it should be, so a program that does it better makes sense. At the moment, GRUB and rEFIt can both do this, but they've both got problems -- GRUB is unreliable on (U)EFI, in my experience; and rEFIt is inflexible.

In my (still somewhat limited) experience, [ELILO](http://elilo.sourceforge.net) is the most reliable EFI boot loader for Linux on UEFI-based systems; however, I've not gotten it to work on my EFI-based Mac Mini. ELILO also can't chainload to another EFI loader, so you're stuck with the firmware's boot selector or another one, such as rEFIt, if you need to select between Linux and a non-Linux OS. You can use ELILO to select between two different Linux installations, though.

> Suppose GPT has 4 separate Ubuntu installations and an EFI System Partition. Is the intentention that there are 4 separate .efi files that can be chosen from the UEFI bios menu? Or is this not clear at this stage?

I can't speak to the intention of the developers in such a specific case. As a practical matter, though, you could do it either way -- set up one boot loader (GRUB 2 or ELILO) with sub-options for each installation or set up separate boot loaders for each installation. The way Ubuntu works by default would probably be much the same as on a BIOS-based computer -- the last Ubuntu system you install (or its GRUB 2 version, really) would take over the boot loader duties for all of the Ubuntu installations.

> And what happens when there are multiple disks and more than one ESP? Does the bios UEFI concatenate their contents into one single menu selection?

It should, yes; however, I've not tested this.

---

