---
title: "Ubuntu does not boot after installation (MBR not correct?)"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by LukeNukem23 on 2018-03-10
Hi,

I just bought a new barebone ([this one]("https://www.amazon.com/UN65U-M023M-VivoMini-Barebones-i3-7100U-integrated/dp/B06WV7NB95/ref=sr_1_fkmr0_2?ie=UTF8&qid=1520711683&sr=8-2-fkmr0&keywords=Asus+Barebone+VivoMini+UN45-VM014M+Mini")) and added a 250 Gig SSD + 8 GB RAM. (The point is that the hardware is entirely new).

I just installed Ubuntu (and after that OpenElec just to compare and I am having exactly the same problem). When I have the Live-Stick plugged in, I can boot the live version from it as well as install from it, when I boot the PC and the stick is plugged in, I can see its boot selection.

Now after I have installed Ubuntu (or OpenElec) and I am trying to boot from the disk all I get is a black screen for 5 seconds and then my PC switches to the EFI config screen.

When load the live version and I do ```
parted -l
``` I can see the SSD is there, partitioned and bootable:

```
Lakka:~ # parted -lModel: Generic Flash Disk (scsi)
Disk /dev/sda: 2037MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  538MB   537MB   fat16        system   legacy_boot, msftdata
 2      538MB   2036MB  1498MB  ext4         primary




Model: Unknown (unknown)
Disk /dev/nvme0n1: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End    Size   File system  Name     Flags
 1      1049kB  538MB  537MB  fat32        primary  boot, legacy_boot, esp
 2      538MB   250GB  250GB  ext4         primary
```

I assume my MBR isn't set properly, could this be? If so, what can I do to diagnose or fix this?

Thank you
Lukas

---

### Post by oldfred on 2018-03-10
New UEFI systems do not use MBR for UEFI boot.
The gpt partitioning does have a MBR, just for protection from old tools, but it can also be used for legacy/BIOS/CSM boot.

Some data is missing on the newer NVMe drives but this shows details on install.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by LukeNukem23 on 2018-03-18
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]It turned out I needed to flash my BIOS, which did not work well with my SSD (it did not really detect it). This was a bug in ASUS' UN45 Model.[/FONT]
[/FONT][/COLOR]

---

### Post by ubfan1 on 2018-03-18
Thanks for sharing your solution.  Under the "Thread Tools" button at the top of the thread, please mark this as "Solved".

---

