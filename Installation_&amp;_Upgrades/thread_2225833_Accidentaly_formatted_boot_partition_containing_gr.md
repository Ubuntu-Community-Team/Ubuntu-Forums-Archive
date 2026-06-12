---
title: "Accidentaly formatted boot partition containing grub"
date: 2014-05-23
forum: Installation &amp; Upgrades
---

### Post by PartisanEntity on 2014-05-23
Hi all,

I have reached new hights in my stupidity and haven't managed to get myself out of this one so far.

I accidentally formatted the partition that contained the GRUB boot loader, so I cannot boot into Ubuntu 14.04 LTS.

Background to the saga:

I have an iMac with OSX and Ubuntu 14.04 LTS installed side by side. And am using REFIND to choose between the two. When I select Ubuntu in refind, I would get the grub boot menu and from there I would select ubuntu to launch Ubuntu 14.04 LTS.

After upgrading OSX to OSX Mavericks I could no longer boot into Ubuntu because I got the error:

```
error: unknown filesystem
grub rescue >
```

(During the upgrade process to OSX Mavericks the OSX Installer added another Recovery HD partition, so I now have 2 of those. I think this lead to the problems with my partition that holds the GRUB loader).

However I then went and, in a moment of insanity, did something silly and dug myself a deeper hole:

I booted using an Ubuntu Live CD, and fired up gparted.

Then without really thinking, I changed the filesystem on the GRUB partition from "unknown" to FAT32, effectively also erasing anything that was on this GRUB partition.

What I have tried so far:

1. Set the "boot" flag on this fat32 partition (sda6)

2. Booted into a Live CD

3. Installed Boot Repair in the Live CD instance and attempted to have it repair the boot options and settings.

But it fails and spits out this as a pastebin link:

[http://paste.ubuntu.com/7505869/](http://paste.ubuntu.com/7505869/) 

One of the problems I noticed is that based on what I read, Boot Repair needs to be in EFI mode to work.

However from what I can tell the Ubuntu Live CD is booting into BIOS mode which I think is the reason that Boot Repair could be failing? If that is indeed the case, I have not figured out how to get the Live CD to boot into EFI mode.

Any help would be appreciated.

---

### Post by oldfred on 2014-05-23
I do not know Mac and what is unique about it.

But you show two efi partitions. While UEFI spec says you can do that, no UEFI system we have seen supports that. Remove boot flag from sda6. Then Boot-Repair may work. I thought it worked even when in BIOS mode if the efi box was ticked. Not sure why in partition listing shows two efi partitions, but blkid only shows one, or is that just your label?

You also are showing a hybrid system. I thought that was only required with Windows has it will only boot in BIOS mode and needs MBR partitioning. Ubuntu will UEFI boot and works from gpt.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
    
It does look like Boot-Repair swapped efi, and 70d6-xxx is the sda1 efi partition.
>  #UUID=F710-71A0    /boot/efi    vfat    defaults    0    1
UUID=70D6-1701    /boot/efi    vfat    defaults    0    1


Script is not showing any efi boot files anywhere, but do not know if it is looking in correct places on a Mac?
Script is hard coded to just look in certain places.

---

