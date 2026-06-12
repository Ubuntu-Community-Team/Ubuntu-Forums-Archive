---
title: "dmraid fails on Intel 82801HR/HH/HO SATA RAID controller with 3 drive RAID0"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Bill F on 2008-07-18
This page led me here.
[https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

Anyway I have a laptop (Clevo D901C) with this controller. (its basically a desktop 965 chipset, with Q6600)
I get the "no raid disks found."
Here is the output of the mentioned command.
```
fdisk -u -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06850684

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104856254    52428096    7  HPFS/NTFS
/dev/sda2       104856255   209712509    52428127+   7  HPFS/NTFS
/dev/sda3       209712510   837436319   313861905    7  HPFS/NTFS
/dev/sda4       837436320  1465160129   313861905    7  HPFS/NTFS
```

After doing "dd if=/dev/sda of=outputfile skip=488395168"
Here is some relevant text I found at the *very end* of the output file, which is attached.
> Intel Raid ISM Cfg Sig. 1.2.01  
21BB0F00WDG18AWApY
21BB0F00WDG0JSMApY
21BB0F00WDG0WXVApY  
Volume0

I really hope I can get some form of 64 bit linux installed on my laptop without destroying my current RAID0.


Edit: I figured out that "Intel Raid ISM Cfg Sig. " is what the program looks for exactly, and it is in the last 2 sectors of the disk.
To fix this I am supposed to edit the isw.h file in the source code and recompile but since I am a n00b programmer I am not sure how to do this with the very complicated source code files.

---

