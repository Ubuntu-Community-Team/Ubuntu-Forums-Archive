---
title: "blank screen LTS 22.04.01 install from safe graphics mode; APU/integrated graphics"
date: 2022-11-18
forum: Installation &amp; Upgrades
---

### Post by ro44444444 on 2022-11-18
I've installed Ubuntu multiple times before on different systems, including LTS 22.04.01 on other (older) systems. I've just built a new PC, and am trying to newly install 22.04.01 LTS on it. The hardware appears to be properly connected, functioning, and testing properly. I can boot into Safe Graphics mode from a live USB, but from there either I am unable to boot to anything except a blank screen.


[LIST]
[*]**OS**
[LIST]
[*](attempting to install) Ubuntu 22.04.01 LTS
[/LIST]
[/LIST]

[LIST]
[*]**HARDWARE**
[LIST]
[*]APU = Ryzen 7 5700G APU, using integrated graphics/HDMI;
[*]motherboard = Gigabyte X570SI Aorus PRO AX;
[*]storage 1 of 2=1 TB NVMe M.2 (for EFI, swap, root, and home partitions);
[*]storage 2 of 2= 2 TB NVMe M.2 (one large partition, ZFS/encrypted file system, with ~1 TB data
[*]DDR4 32 GB x 2
[*]
[/LIST]
[/LIST]

[LIST]
[*]**PROBLEM**
[LIST]
[*]after seemingly completing an install booting from Safe Graphics mode via live USB, restart/reboot hangs at a cursor. Upon hard reset, I get the code below, then an endless blank screen.
[/LIST]
[/LIST]

[LIST]
[*]**OUTPUT**
[LIST]
[*]**&#8203;**When I boot after completing the USB install, I get slightly varying lines of code, like this:
[/LIST]
[/LIST]

```
    /: recovering journal 
    /: Clearing orphaned inode 17432778 (uid=1000, gid=1000, mode=0100664, size=32768) 
    /: Clearing orphaned inode 17432769 (uid=1000, gid=1000, mode=0100600, size=64) 
    /: clean, 214427/56926208 files, 6084315/227675136 blocks 
    [      4.197346] mtd device must be supplied (device name is empty) 
    [      4.478930] mtd device must be supplied (device name is empty) 
    [      4.501321] mt7921e 0000:05:00.0: ASIC revision: 79610010

```


[LIST=|INDENT=2]
[*]When I boot from USB in Safe Graphics mode, I get lines like this, then after a few seconds I get to a usable desktop:
[/LIST]

```
[       3.313105]  [drm:amdgpu_init [amdgpu] *ERROR* VGACON disabled amdgpu kernel modesetting.
[     10.254479] mtd device must be supplied (device name is empty)

```

[LIST]
[*][B]BIOS SETTINGS (partial)
[/B]
[LIST]
[*]BIOS Version F2, BIOS date 01/04/2022; BIOS ID 8AVMR008

[*]...>*Settings>IO Ports> Initial Display Output* = "_IGD Video_" (default was "PCIe 1 Slot").
[*]...>*Settings>IO Ports>Integrated Graphics* = _Forces_ (default was "Auto", also "Disabled" option).
[*]...>*Settings>IO Ports>NVMe Configuration* shows both drives correctly, _both drives pass health tests_.
[*]...>*Settings>IO Ports>SATA Configuration>NVMe RAID* *Mode *= _Disabled_.
[*]...>*Settings>IO Ports>SATA Configuration>SATA Mode* = AHCI (no hardware is installed in any SATA port.)
[*]...>*Boot>CSM Support* is _Disabled_.
[*]...>*Boot>Fast Boot* is _Disabled_.
[*]...>*Tweaker>XMP* is _Disabled_.
[/LIST]
[/LIST]

[LIST]
[*][B]THINGS I'VE TRIED TO FIX IT
[/B]
[LIST]
[*]Verified and authenticated the install media.
[*]Used different install media.
[*]Used different Linux distro live installs.
[*]Tweaked BIOS settings relating to Integrated Graphics, NVMe RAID, and SATA RAID,
[*]ried a lot of tweaks, including different Linux live USB installs. I've reset the BIOS to default settings, but have to change two Integrated graphics settings to be able to boot to the live USB:
[/LIST]
[/LIST]

[LIST]
[*]**CURRENT TROUBLESHOOTING OPTIONS**
[LIST]
[*]**&#8203;**Can access and change BIOS settings.
[*]Can run Ubuntu in safe graphics mode from USB.
[*]Can boot to grub command line.
[/LIST]
[/LIST]

---

### Post by MAFoElffen on 2022-11-20
Have you tried booting with a 'nomodeset" boot parameter, before checking additional drivers for an appropriate graphics driver?

---

