---
title: "pre-installed Windows 8 boot fails after Xubuntu 13.10 boot fixed"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by silentstone on 2014-09-06
I would like to dualboot Xubuntu 13.10 and Windows 8 from the GRUB2 menu without reinstalling Windows 8; I don't have any Windows reinstall media besides the Recovery partition on the internal HDD.

I'm not new to Linux or Ubuntu or dualbooting, but the *UEFI* stuff confounded me; so, I picked my way through the initial installation of _Xubuntu 13.10_ on an Asus laptop with _Windows 8_ 64-bit pre-installed.  Nevertheless, I ran into a problem immediately in that the Installer never detected the Windows installation.  I chose the 'Something Else' option and manually configured some partitions behind the Windows, keeping the Linux boot partition separate from Windows's, and I may have assigned a 'boot' flag to Linux's boot partition.

On reboot, Windows 8 booted immediately with no sign of Linux.  However, after fiddling with the *System Setup* and manually pointing to Linux's .efi files, Xubuntu booted.  But now, no Windows boot.

Currently, all the Windows boot features were disabled (*FastBoot, hibernation*), the single hard drive is *UEFI* set, *SecureBoot*-enabled, boot manager is **GRUB2** with functioning Linux entries and non-functioning Windows entries.  **Boot-Repair** was installed and run from the HDD-installed Xubuntu system; I only used it to generate a *BootInfo Summary* here: [http://paste.ubuntu.com/8273250/](http://paste.ubuntu.com/8273250/)

Some things stand out: sda5 reports two different starting points, a warning about the Linux boot partition being too far from the disk's start...

But where do I go from here?

---

### Post by yancek on 2014-09-06
You can set the boot flag on the windows partition with GParted.  I don't use EFI so can't help with that.  I wouldn't put too much effort into it as Xubuntu 13.10 is not longer supported and you won't be able to get updates or new software using the standard methods.

---

### Post by silentstone on 2014-09-07
The Linux installation is important:  I keep all my stuff there :)  IIRC, there can only be one boot-flagged partition on a GPT drive; if Windows is it, all the Linux access will be lost at boot because the Windows boot manager doesn't list the Linux at all.  
     
But I know the Windows boot files are still functional because the pre-OS/System Setup's boot menu (F12 on boot) points to a functional "Windows Boot Manager" entry!  Which I just discovered.  Anyway, does that make GRUB the problem?

---

### Post by fantab on 2014-09-07
```
parted -l:

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  420MB   419MB   ntfs            Basic data partition          hidden, diag
**2      420MB   735MB   315MB   fat32           [COLOR=#b22222]EFI system partition[/COLOR]          boot**
3      735MB   869MB   134MB                   Microsoft reserved partition  msftres
4      869MB   87.1GB  86.3GB  ntfs            Basic data partition          msftdata
**5      87.1GB  87.4GB  276MB   fat32           Basic data partition          boot**
6      87.4GB  473GB   386GB   ext4            Basic data partition          msftdata
9      473GB   481GB   8277MB  linux-swap(v1)
7      481GB   482GB   367MB   ntfs                                          hidden, diag
8      482GB   500GB   18.3GB  ntfs            Basic data partition          hidden, diag
```

Remove the 'boot' flag from the 5th data partition... 
There can be only one ESP [EFI system partition], your attempt to create a second fat32 5th partition was in vain.

```
efibootmgr -v
BootCurrent: 0005
Timeout: 2 seconds
BootOrder: 0005,0001,0000,0002
Boot0000* Windows Boot Manager    HD(2,c8800,96000,6af53f04-90f4-4d4c-ad70-aa398c633b66)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0001* HDD0:     HD(2,c8800,96000,6af53f04-90f4-4d4c-ad70-aa398c633b66)File(EFIubuntugrubx64.efi)RC
Boot0002* xubuntu    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,c8800,96000,6af53f04-90f4-4d4c-ad70-aa398c633b66)File(EFIubuntugrubx64.efi)A01 ..
Boot0004* MATSHITA DVD-RAM UJ8E1              BIOS(3,500,1f)................-...........A......#...................................
Boot0005* ubuntu    HD(2,c8800,96000,6af53f04-90f4-4d4c-ad70-aa398c633b66)File(EFIubuntushimx64.efi)
```

> Recommended-Repair
This setting would reinstall the grub-efi-amd64-signed of sda6, using the following options: sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

Run the 'Recommended-Repair' offered by Boot-Repair tool it can fix some minor Windows boot issues.

However if you have discovered the one-time-boot key to boot Windows and are happy with it..... then so be it.
No issues.

---

### Post by Bucky Ball on 2014-09-07
I hope you have some luck, but just thought I'd direct you to this for future reference:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

13.10 is no longer supported and there will not be much support available here, if any, if you have problems specifically related to it. Better to go with 14.04 LTS, a long-term support release supported until April 2019.

---

