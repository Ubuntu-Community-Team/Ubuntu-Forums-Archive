---
title: "Made external drive bootable both UEFI and BIOS, Xubuntu 18.04.1"
date: 2019-01-31
forum: Installation &amp; Upgrades
---

### Post by 4dummies on 2019-01-31
I had a lot of trouble applying answers from previous versions of ?buntu, and had to thrash around quite a bit until I found the easy way.  So I'm posting my solution.

The goal was a working Xubuntu (not installation medium) on an external drive (I used pendrives, both Mushkin and Kingston), that would boot on hardware that supported only UEFI and also on hardware that only supported BIOS boot.  The usual installation ISOs from Canonical can do either one, but I was unable to convert either one to support the other mode of booting.  However, noting what it did do that worked, and the differences, gave me the ideas the way I'm presenting here.

NOTE: In all steps, I ensured the medium I was configuring was seen as /dev/sda; this was in accordance with advice from previous answers, but may no longer be necessary.  On the machine I was using, this was achieved by detaching the HDD and choosing which USB ports were used for which drive.

Overview: First partition the drive.  Second, boot the installation medium in UEFI, and install using the "something else" option.  Third, boot the installation medium in BIOS, and install using the "something else" option.  I did this on an old HP Compaq Pro 6305 whose boot menu allows choosing both the medium and the mode.  There are surely other ways to get the same results.

One oddity I noticed was that when installing for UEFI, the installation starts the EFI partition a full 32 MB into the drive, leaving a gap of 31MB or so that's not very useful.  My attempts to shrink that gap led to nothing but failure to boot.  There may be a way, but I did not find it.  I did put the BIOS-grup partition in there, but that's just 1MB.

So more details on the three steps:

**[SIZE=4]Partition the drive:[/SIZE] **I used gparted, but you can probably use gdisk.  Here's what it looks like right now:
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2           65535         1048559   480.0 MiB   EF00  EFI System Partition
   3         1048576         2097151   512.0 MiB   8300  boot
   4         2097152        69206015   32.0 GiB    8300  root
   5       232343552       234440703   1024.0 MiB  8200  swap
```
I get the codes in gparted by managing flags.  EF02 corresponds to the gparted flag "bios_grub".  EF00 corresponds to flag "esp".

I made the root and boot partitions EXT4, but I gather that EXT2 might be a better choice on flash media.

**[SIZE=4]Install UEFI[/SIZE] **
I installed the same system twice.  Following advice from 16.04 and 14.04, I made sure to boot the installation medium the same way I wanted the system installed.  

I used the "something else" choice for the kind of install. For the UEFI version, I assigned three partitions to be mounted, and set them to be formatted:
[LIST]
[*]partition 4 as /
[*]partition 3 as /boot
[*]partition 2 as /boot/efi
[/LIST]

For everything else, I used defaults because what was presented to me made sense.

Check that the results boot in UEFI mode (it will probably fail in BIOS mode; no worries)

**[SIZE=4]Install for BIOS boot[/SIZE] **
Rebooting the installation medium in BIOS (legacy) mode, I again used the "something else" choice, but only assigned two parttions to be mounted, and did NOT set them to be formatted:
[LIST]
[*]partition 4 as /
[*]partition 3 as /boot
[/LIST]

Everything else was exactly as for the UEFI booting.
At the end, the installer complained about difficulty installing things because of what was already there.  I ignored it and have not regretted it so far.

**[SIZE=4]Results and oddities[/SIZE] **
The resulting stick still booted in UEFI mode.  On my particular machine, it would not boot in BIOS mode.  Oddly, it did boot that way on other machines, or seemed to.  I changed the flags and the code on the EFI partition (CODE 8301, "Linux Reserved). and it still booted in BIOS mode, but not in UEFI mode.  Oddly, I could not then restore UEFI booting, so I had to restore a complete dd-copy backup of the pendrive.  I'd love to know why.

---

### Post by C.S.Cameron on 2019-01-31
Another method that makes a Full install external drive that boots both BIOS and UEFI:
[https://askubuntu.com/questions/1107281/how-do-i-create-a-bootable-live-usb-that-uses-ext4-opposed-to-iso-9660-squashfs/1107334#1107334](https://askubuntu.com/questions/1107281/how-do-i-create-a-bootable-live-usb-that-uses-ext4-opposed-to-iso-9660-squashfs/1107334#1107334)

---

