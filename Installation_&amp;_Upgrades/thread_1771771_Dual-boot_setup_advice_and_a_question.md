---
title: "Dual-boot setup advice and a question"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by TheDarkCanuck on 2011-05-30
Hi all,

I'm an extremely new ubuntu user, having only tried it from the live cd and a little through virtualbox.  That said, I will be buying a new computer soon and would like to use ubuntu as my primary OS--however I will also need to run windows for gaming. I am hoping to get some advice regarding how best to setup my new computer. As near as I can tell I have at least three options:

1. Include 2 ssds in the new machine, install windows on one, ubuntu on the other, have a shared 3rd drive for music, documents, pics, etc, and dual-boot.

2. Have a single ssd, partition it, have a shared media drive, dual-boot etc etc.

3. Have windows as the primary OS, and run ubuntu through some sort of virtualization software. 

My aim is to use ubuntu for pretty much everything save for gaming (which i would like to be running off a ssd). Any thoughts about which setup would serve me best? My inclination is to go with option 1 above, but I really do not know the pros and cons of doing so. Happy to be told that one of the other options would serve me better.

One additional question: there is a good chance I will be looking at having an nvidia surround setup for gaming--meaning 3 monitors--and was wondering whether or not a 3 monitor set-up can be run with ubuntu without too much trouble.

Thanks for any help.

---

### Post by TheDarkCanuck on 2011-05-31
Quick follow-up question: I assume that wubi is not meant for long term use, but rather as a means to preview ubuntu only. So it is not truly an option for me, corect?

---

### Post by baarn on 2011-05-31
i dont know about wubi, name sounds stupid... ;)

you need one drive and partition it correctly.

"safest" method for windows usage is as follows:
windows7 installs a hidden boot partition about 100MB if it is able to, you should windows do that, because its a safety measure to not have boot-crtitical stuff visible to the whole system.
so right now there are two possible primary partitions blocked by windows.
i am not sure if its possible to tell windows to not use the whole drive if its not pre-formated, but i think it is... if so leave some space at the end of the drive you want for shared stuff and linux.

afterwards install linux, when asked about partitioning your drive create another primary partition (about 100MB) thats your /boot, toggle the bootable flag on it (causing it to be booted, instead of booting the win-boot partition).
last "primary partition" will actually be an extended partition housing all partitions (logical ones) you need for linux and spare space.

so your partition table would look like this
sda1: winboot
sda2: win (C:)
sda3: /boot
sda4: extended
sda5: nfts partition? (D:)
sda6: /
sda7: swap
sda8: /home

if you want you can create some more partitions housing /tmp /usr and /var, the advantage of that is that fragmentation on one partition will have no affect to the other partitions, disadvantage is that you have to guess how much space each of those will need.

edit: you can aswell use the windows bootloader to boot your linux, but i am not sure how that works and think you will need grub aswell, only difference should be that you dont tell grub to be able to chainload into windows, you only tell windows to load grub... or something like that. and you dont toggle bootable flags on linux /boot but on winboot... i for my part prefer grub ;)

---

### Post by oldfred on 2011-05-31
If price of two SSDs in not an issue I would do that. I would probably prefer to even use one SSD for windows since you seem to want the speed for gaming and leave Ubuntu on a rotating drive if two SSDs is to much.

I greatly prefer to have each operating system on a separate device and make each device bootable without the other. SSDs may change that slightly but I have not done that (yet).

You may also have additional complications with a very new system. New systems are starting to be UEFI which windows 7 64 bit will work with, but grub2 efi boot system seems to have some configuration issues with some systems. Most of these new system also will work in BIOS mode, so that may be an alternative. But with large drives gpt partitioning is better than MBR, but Win7 will only boot with UEFI with gpt and Ubuntu works with gpt with UEFI (Some work ok)  or BIOS.

Installing Ubuntu in Hard Disk Two (or more) internal or external Maverick screens shown
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)


It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

