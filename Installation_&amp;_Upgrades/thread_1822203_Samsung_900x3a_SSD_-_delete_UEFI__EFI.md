---
title: "Samsung 900x3a SSD - delete UEFI / EFI ?"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by Findarato on 2011-08-10
Hello,

I am thinking of re-installing my ubuntu machine (Samsung 900x3a) and would like it to boot in ubuntu directly. However, I have no idea what this UEFI booting really is and I know it is installed on a partition which I would like to wipe. Would my machine work if I wiped that or is it essential to the behaviour of the machine?

---

### Post by YesWeCan on 2011-08-10
UEFI is a new-fangled boot system that replaces the old-fashioned MBR boot system. But it is complicated and Ubuntu doesn't support it without some crafting (as I understand it) and you only need it if you are trying to boot an OS on a GPT formatted disk and not even then as Grub has a hack to get around it. Your bios should be configurable to use either method.

Anyhow, what's on your disks right now? Would you download this and post the RESULTS.txt here inside code tags?
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by srs5694 on 2011-08-10
UEFI is a (relatively) new type of firmware that supports, as YesWeCan says, a new boot method. In the old BIOS-style boot system, boot code is placed in the Master Boot Record (MBR) of the hard disk, along with a partition table. The MBR boot code area is quite small (440 bytes), so BIOS boot loaders tend either to be very simplistic (such as the DOS/Windows boot loader) or to rely on supplemental code elsewhere (such as GRUB 2, which places extra code in the officially unallocated sectors that immediately follow the MBR).

UEFI, OTOH, was designed to use boot loaders that are stored in a special partition, known as the EFI System Partition (ESP). Because boot loaders are files in a filesystem, they can be quite large in size and they can be much easier to manage -- you can install them, delete them, rename them, etc., using ordinary filesystem management tools like cp, rm, mv, etc. Chances are the ESP is the "partition which [you] would like to wipe". Erasing the files in the ESP will erase your boot loaders, rendering all your installed OSes unbootable. This is fine if you plan to re-install everything, but if you want to keep any currently-installed OS working, you shouldn't erase the ESP. Also, you shouldn't completely delete the ESP from the partition table, since UEFI requires it to boot. (At least in UEFI mode; most or all UEFIs have a BIOS compatibility mode that enables the computer to boot using BIOS boot loaders.)

The Boot Info Script output that YesWeCan requested can provide additional information on your current setup; however, be aware that the Boot Info Script doesn't understand UEFI booting, so if you're currently booting any OS in UEFI mode, the Boot Info Script output will present an incomplete picture.

Ubuntu can install and boot in UEFI mode; however, this support still has some bugs and limitations, including:


[list]
[*]If you select the "other" partitioning option, Ubuntu won't automatically detect, much less create, your ESP; you must flag it as such yourself. (IIRC, the Ubuntu installer calls it the "EFI boot partition.")
[*]Ubuntu erases the ESP and writes a fresh FAT16 filesystem to it. This is a problem for two reasons:

[list]
[*]If you install Ubuntu after another OS, you'll lose the other OS's EFI boot loader, rendering it unbootable and in need of repair.
[*]The UEFI spec says that the ESP must have a FAT32 filesystem. Most OSes are fine with FAT16 instead, but the Windows 7 installer insists on FAT32 and does weird things if it sees FAT16.
[/list]

[*]In my experience, the EFI version of GRUB 2 that Ubuntu uses is flaky and unreliable; sometimes it works, but sometimes it doesn't. I've found [ELILO](http://elilo.sourceforge.net) to be more reliable on the UEFI systems I've used; however, my sample is limited.
[/list]


Sad to say, currently (version 11.04) Ubuntu's UEFI support should really only be used by experts or those who must use it for one reason or another. It'll probably improve in the future, though. When that happens and once people are familiar with it, UEFI booting is likely to be easier to manage than BIOS booting, since UEFI relies on files in a filesystem rather than code written directly to the MBR or other parts of the disk that can't be accessed as files.

---

### Post by YesWeCan on 2011-08-10
Nice summary.

Just to add that GPT and UEFI are, I suppose, independent systems: one is for partitioning and the other for booting. That is, a Guid Partition Table is a modern alternative to the very old bios/MBR partition table which has address limitations when the disk is bigger than 2TB. Either can have many partitions: the bios/MBR system achieves this by daisy-chaining partition tables and the GPT system achieves this by having a single, huge partition table.

The current Ubuntu installer can't install Grub to a GPT for several reasons but I guess the main one is that Grub usually occupies the sectors that the new GPT partition table uses.

---

### Post by srs5694 on 2011-08-10
> **YesWeCan said:**
> Just to add that GPT and UEFI are, I suppose, independent systems: one is for partitioning and the other for booting. That is, a Guid Partition Table is a modern alternative to the very old bios/MBR partition table which has address limitations when the disk is bigger than 2TB. Either can have many partitions: the bios/MBR system achieves this by daisy-chaining partition tables and the GPT system achieves this by having a single, huge partition table.

This is correct, but with one important caveat: Windows ties the firmware type and the partition table type together, at least for boot disks. Under Windows, if you use BIOS to boot, you *must* use MBR as the partition table type, and if you use UEFI to boot, you *must* use GPT. (You can use either partition table type for non-boot disks, though, at least for Vista and later.) This is a Windows limitation, though. Linux, FreeBSD, and some other modern operating systems enable you to use either GPT or MBR with either BIOS or UEFI style booting. Thus, if you want to dual-boot with Windows, you should choose your partition table type depending on the boot method you use for Windows. On a Linux-only system, though, you can use whichever partition table type you like.

> The current Ubuntu installer can't install Grub to a GPT for several reasons but I guess the main one is that Grub usually occupies the sectors that the new GPT partition table uses.

This isn't correct. I've installed Ubuntu to GPT disks with no problems, on both BIOS-based and UEFI-based systems. The caveat is that if you install to a GPT disk on a BIOS-based computer, you may need to have a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to make GRUB happy. (Theoretically, it's not required; but there are situations in which it's a practical necessity.) I don't recall offhand under what, if any, circumstances the Ubuntu installer creates a BIOS Boot Partition, but I know it's not automatically created all of the time, since I've seen several posts from people who've had problems because of its non-creation.

Under EFI/UEFI, as I stated before, an [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) is required. This is different from a BIOS Boot Partition, but the two are similar in that they both hold boot loader code.

If you're in doubt about whether your system uses BIOS or UEFI, or if you know your computer supports both boot methods and you're not sure which you'll ultimately want to use, it's safest to create both a BIOS Boot Partition and an ESP. Either can be any partition number and can be located anywhere on the disk, except that a BIOS Boot Partition probably has to reside below the 2 TiB mark (or possibly lower, depending on your BIOS's limits). Conventionally, the ESP is the first partition, so you might want to make it that, and make it ~200-250 MiB. The BIOS Boot Partition can be tiny, but given modern partition alignment practices, 1 MiB makes a good size.

---

### Post by YesWeCan on 2011-08-10
> **srs5694 said:**
> This isn't correct. I've installed Ubuntu to GPT disks with no problems, on both BIOS-based and UEFI-based systems. The caveat is that if you install to a GPT disk on a BIOS-based computer, you may need to have a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to make GRUB happy. (Theoretically, it's not required; but there are situations in which it's a practical necessity.) I don't recall offhand under what, if any, circumstances the Ubuntu installer creates a BIOS Boot Partition, but I know it's not automatically created all of the time, since I've seen several posts from people who've had problems because of its non-creation.
This is not correct. In the absence of a bios-grub partition the Grub program has to be installed (at least if one wants it to be reliable) to the MBR area, which will corrupt a GPT disk. A special partition is required in theory as well as practice. The nature of the Ubuntu installer may be changing gradually but we have seen many problems with it when trying to install to a GPT disk.
What I am not sure about is whether and which versions of the Ubuntu installer generate a bios-grub partition automatically, if any. I suspect the whole thing is rather half-baked right now and ordinary mortals should not be trying to install Ubuntu on GPT disks.
BTW it would be very useful to be able to make a bios-grub partition on an MBR disk too, but this is deliberately not allowed.

---

### Post by psusi on 2011-08-10
> **YesWeCan said:**
> This is not correct. In the absence of a bios-grub partition the Grub program has to be installed (at least if one wants it to be reliable) to the MBR area, which will corrupt a GPT disk. A special partition is required in theory as well as practice. The nature of the Ubuntu installer may be changing gradually but we have seen many problems with it when trying to install to a GPT disk.

This is not correct ;)

Grub will never corrupt the GPT.  If it can't find the bios_grub partition, then it will normally refuse to install, but you can use --force to make it link the MBR directly to the core.img in the filesystem, but this is NOT recommended.

> **YesWeCan said:**
> BTW it would be very useful to be able to make a bios-grub partition on an MBR disk too, but this is deliberately not allowed.

It isn't deliberately not allowed, there just is no MBR partition type code for it.  It also wouldn't be useful since without the GPT in the way, the core image fits nicely right after the MBR.  That area going away was the whole reason the bios_grub partition was created in the first place.

---

### Post by YesWeCan on 2011-08-10
> **psusi said:**
> This is not correct ;)

Grub will never corrupt the GPT.  If it can't find the bios_grub partition, then it will normally refuse to install, but you can use --force to make it link the MBR directly to the core.img in the filesystem, but this is NOT recommended.
That is not correct! :P
But only in the sense that I don't think that is what I said. My point is that Grub cannot be installed to a GPT without a bios-grub partition exactly because it would corrupt the GPT table.

> It isn't deliberately not allowed, there just is no MBR partition type code for it.  It also wouldn't be useful since without the GPT in the way, the core image fits nicely right after the MBR.  That area going away was the whole reason the bios_grub partition was created in the first place.
There is a partition type code for it - or could be one. But I haven't been able with Disk Utility or GParted to create a partition of this type.
If you spent as much time as I have dealing with same-disk dual boot problems that are caused by Grub corrupting the MBR area you might agree with me that Grub should be kept out of it. A bios-grub partition can be logical and so everything linux related could be kept cleanly inside an extended partition, for example. I really think it would save a lot of grief especially for a lot of Windows users transitioning to Ubuntu. I don't understand why this wasn't built in to Grub2 from the start rather than being forced by GPT.

---

### Post by psusi on 2011-08-10
> **YesWeCan said:**
> That is not correct! :P
But only in the sense that I don't think that is what I said. My point is that Grub cannot be installed to a GPT without a bios-grub partition exactly because it would corrupt the GPT table.

Except that it can fall back to using the old blocklist method instead of embedding the core image after the MBR... you just have to use --force and it isn't recommended.


> **YesWeCan said:**
> There is a partition type code for it - or could be one. But I haven't been able with Disk Utility or GParted to create a partition of this type.

I suppose you could but but the grub maintainers saw no reason to do so, so they didn't bother.  It's also pretty hard to pick a code that isn't already in use somewhere.

> **YesWeCan said:**
> If you spent as much time as I have dealing with same-disk dual boot problems that are caused by Grub corrupting the MBR area you might agree with me that Grub should be kept out of it.

Huh?  It's OTHER programs that corrupt the MBR area and mess up grub, most notably a small handful of windows programs that think they can use that area to store copy protection junk.  The known ones have been worked around in current versions of grub by having it avoid using the particular sectors those programs mess up.

---

### Post by srs5694 on 2011-08-10
> **YesWeCan said:**
> [quote=srs5694]This isn't correct. I've installed Ubuntu to GPT disks with no problems,  on both BIOS-based and UEFI-based systems. The caveat is that if you  install to a GPT disk on a BIOS-based computer, you may need to have a [BIOS Boot Partition]("http://en.wikipedia.org/wiki/BIOS_Boot_partition")  to make GRUB happy. (Theoretically, it's not required; but there are  situations in which it's a practical necessity.) I don't recall offhand  under what, if any, circumstances the Ubuntu installer creates a BIOS  Boot Partition, but I know it's not automatically created all of the  time, since I've seen several posts from people who've had problems  because of its non-creation.This is not correct. In the absence of a bios-grub partition the Grub program has to be installed (at least if one wants it to be reliable) to the MBR area, which will corrupt a GPT disk. A special partition is required in theory as well as practice.[/QUOTE]

The main point of my post was this statement of yours:

> **YesWeCan]The current Ubuntu installer can't install Grub to a GPT for several  reasons but I guess the main one is that Grub usually occupies the  sectors that the new GPT partition table uses.[/quote]

As stated, this is simply false said:**
> There is a partition type code for it - or could be one. But I haven't  been able with Disk Utility or GParted to create a partition of this  type.

There's a big difference between "is" and "could be." It's hardly surprising that you can't set such a type code with existing tools when there is no agreed-upon code for such a partition or current tools that would use it.

That said, we are talking about open source software. Since you feel so strongly about it, I suggest (in all seriousness) that you try modifying GRUB 2 to support this option and submit a patch. If it's accepted, do the same for Linux fdisk and for libparted. (You can set any type code you like with fdisk, so you can test and use a GRUB 2 patch without patching any partitioning tool. Patches to partitioning tools like libparted, and probably the Ubuntu installer, would be required to use such a partition when installing an OS.)

---

