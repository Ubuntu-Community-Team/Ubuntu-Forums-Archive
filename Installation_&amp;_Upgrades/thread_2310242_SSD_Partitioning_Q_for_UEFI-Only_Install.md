---
title: "SSD Partitioning Q for UEFI-Only Install"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by dswaugh on 2016-01-17
I notice in oldfred's [partitioning scheme]("http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413") that he includes "bios_grub" and "swap" partitions on an SSD install. Just wondering if one can exclude these partitions if doing a UEFI-only install of 15.10 on a 256GB SSD (on hardware that includes 8GB of RAM). Probably a stupid question. If so, sorry.

---

### Post by Dennis N on 2016-01-17
You don't need a bios_grub partition if you plan UEFI installs only (like me). I do create one swap partition on one drive only, no matter how many drives.

---

### Post by ajgreeny on 2016-01-17
> **dswaugh said:**
> I notice in oldfred's [partitioning scheme]("http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413") that he includes "bios_grub" and "swap" partitions on an SSD install. Just wondering if one can exclude these partitions if doing a UEFI-only install of 15.10 on a 256GB SSD (on hardware that includes 8GB of RAM). Probably a stupid question. If so, sorry.
If I remember correctly oldfred has been using GPT partitions for many years, not in a UEFI system, but one with an MBR BIOS.  He has, however always created the very small bios-grub partition which is essential if you have GPT partitions on a BIOS mode installation, and also a larger (100 - 200MB) EFGI partition which is absolutely necessary if using UEFI boot mode.

Regarding swap, there really is no single answer.  With 8GB ram I suspect that swap will seldom, if ever, be needed or used.  But as we do not know how you use your computer there is no way to be certain of this and many users, even with huge RAM sizes still create a small, eg 2GB swap partition, for peace of mind.  Like you I think swap on an SSD is still possibly problematic, even though SSDs are now apparently as hard wearing as spinning disk types, but as I have no personal experience of an SSD I can not give you a full answer to this query.  If you have a separate spinning disk for data storage I would, however, recommend that you put swap on that.

---

### Post by oldfred on 2016-01-17
Oldfred just is in the habit of having both ESP & bios_grub partitions. Neither are large relative to newer drives, and gives flexibility. If UEFI only you do not need the bios_grub. And a bios_grub can be anywhere on a drive.
But an ESP is supposed to be near beginning of drive, so once I thought I might convert to UEFI, I started adding both partitions to every new or reformatted drive as gpt.

If you have 8GB of RAM, you will not use swap, so it does not matter where it is. 

Some also suggest that you have some unallocated space on SSD, so SSD can manage itself better. Do not know details.

---

### Post by Tod Merley on 2016-01-18
> **dswaugh said:**
> I notice in oldfred's [partitioning scheme]("http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413") that he includes "bios_grub" and "swap" partitions on an SSD install. Just wondering if one can exclude these partitions if doing a UEFI-only install of 15.10 on a 256GB SSD (on hardware that includes 8GB of RAM). Probably a stupid question. If so, sorry.

I only know what I recently did. Note that regarding the hardware[1] a 120GB SSD was changed out for the original drive about a year into service.

With the bios set to factory defaults (secure boot UEFI) and choosing to erase and use the entire disk the installer partitioned as follows (note the EFI partition):

Response to sudo fdisk -l      [note: UUID changed]
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0F24C2F3-0682-4288-8F9B-1E53204323E1

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 226899967 225849344 107.7G Linux filesystem
/dev/sda3  226899968 234440703   7540736   3.6G Linux swap

A couple of strange things.  The DVD took an unusually long time to load.  And, after the install was completed of course the &#8220;reboot or continue&#8221; dialog was present (the installer was run from the &#8220;testing&#8221; live environment).  From pressing the &#8220;reboot&#8221; button to sign on in the new environment took about a half an hour.  At about 40 seconds the DVD popped out and at about ten minutes I removed the disk, closed the try, and pressed &#8220;enter&#8221;.  The screen showed what looked like a bit of boot up activity and no prompt to deal with the disk.  And I really do mean that it took a bit over thirty minutes to finally make it to first boot.  Boot times thereafter were normal.

The hardware[1] was purchased in 2013.

[1] At least very similar to an HP 2000-2D49WM

---

