---
title: "live CD/USB not working in UEFI system"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by drunken_sapo on 2012-08-28
Dear all,
            I just bought a new desktop PC with the following specs: 
Video Card: PCI EXPRESS GT440 1GB DDR3 EVGA
CPU I5 3450
MAINBOARD INTEL DZ77SL-50K  OEM HDMI SIN VGA
The 1Tb SATA drive is unpartitioned, I think, just as I got it out of the box.

I have the 12.04.1 amd64 ISO image burnt into a CD and also created a live USB stick.
I've tried enabling and disabling UEFI in the BIOS menu, and tried booting both live CDs and live USB with and without UEFI (because my boot menu allows me too choose).
In the BIOS UEFI enabled+UEFI boot option, I get to the GRUB menu offering: 
"try ubuntu without installing"
"Install ubuntu"
"check disc for defects"

None of these options works, as soon as I pick one option, my system crashes and reboots.

Just for the sake of testing, I also tried to install a windows 7 32 bits, and the boot process advanced up to a point that also crashed.

I've been reading a lot, and many people says that you need an ESP before installing, which could be created with a live USB. My problem is that my HDD is empty and the live USB won't boot, so I'm kinda stuck.

All  the information I got out there is overly complicated and confusing. Is there any simple an safe procedure to install? Should I download a different ISO version?

Thanks in advance.
Best,
       Juan

---

### Post by oldfred on 2012-08-28
I am afraid the UEFI has complicated things.

Did you download the 64 bit version? The 32bit version does not have efi boot.

If you are going to dual boot you need to plan partitions in advance. The very first partition must be the efi partition, Windows wants several and then best to install Ubuntu with several partitions.  With UEFI you use gpt partitioning not MBR(msdos). With gpt partitioning Windows will only boot in UEFI mode. Ubuntu can boot from MBR or gpt with either BIOS or UEFI.

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux.

PC's boot menu, the DVD drive showed up twice: once prefixed with UEFI, once with BIOS.
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)

Some that made it work:
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Windows partitions, I do not know details.
Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

