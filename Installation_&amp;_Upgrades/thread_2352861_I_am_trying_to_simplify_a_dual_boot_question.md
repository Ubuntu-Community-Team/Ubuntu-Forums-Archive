---
title: "I am trying to simplify a dual boot question"
date: 2017-02-16
forum: Installation &amp; Upgrades
---

### Post by mangurian2 on 2017-02-16
Objective:  I want to be able to boot to Ubuntu on an external hard drive, only when that drive is plugged into my USB port.

Absolute constraint:  The [COLOR=#ff0000]**ONLY **[/COLOR]change to my current Windows 10 (64 bit) system will be that the bios/UEFI will first look for a bootable external 100 Gig hard drive **[COLOR=#ff0000]PARTITION [/COLOR]**before booting to the internal Windows HD.

1.  Can that be done?
2.  Other than changing my boot order, what steps must I take?

I am sure this has been answered many times, but I find it difficult to crawl through info about grub and bootloaders which seem to over-complicate what I am trying here.  Perhaps I am too easily confused.  I just don't want to screw up my current system, so I need plain English instructions.  I am very anxious to use Ubuntu again after many years away from it.

Many thanks for any help.

---

### Post by oldfred on 2017-02-16
That would be the default, if UEFI. 
If BIOS, you would have to install grub2's bootloader to external & set BIOS to boot external first.
And you have to use Something Else install option to install to second drive and chose your own partitions. I prefer to partition in advance with gparted.

Grub only installs to the ESP - efi system partition on drive set as sda or usually your Windows internal drive.
And it will set Ubuntu entry as first in UEFI boot order, and you should then have Windows as second in boot order.
Windows updates may reset Windows to first in boot order, so you just have to reset ubuntu to first.
And some brands of computers make it more difficult, as they only boot "Windows Boot Manager" by description.

As long as you do not want to separately boot the external drive from any other system, that will work.
If you want it to work on other systems, then you have to copy files.

Best to configure external drive with ESP ( and maybe bios_grub) so later you could configure it to boot on its own.
I prefer to make every drive, including larger flash drives as bootable. 

Be sure to make external drive gpt partitioned.
Make first two partitions the ESP & bios_grub.

 Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

        Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI) 

Then add whatever partitions you want, /, /home, /mnt/data (either ext4 or NTFS or two partitions), swap.  I often add a /mnt/backup on every drive to have some data from other drive and a separate partition of all my ISO.

---

