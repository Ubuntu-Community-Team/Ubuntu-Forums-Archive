---
title: "boot repair analysis"
date: 2023-03-03
forum: Installation &amp; Upgrades
---

### Post by hickeym21 on 2023-03-03
I have a dell xps 9310 laptop that came with windows installed. About two years ago, I installed linux from a USB. I mostly use Linux, but every few months I need to boot up windows for a work problem. Recently, when I tried to boot up Windows, it asked for my bitlocker key. I'm not sure why it asked for this key. The screen that asked for my bitlocker key offered an option to redownload windows, so I chose that. It appeared to be downloading windows, but when the computer rebooted, it took me to the grub terminal. I tried exiting, but the computer just restarted and brought me to the same terminal. If I press f12 while booting up, it brings up One-Time Boot Settings, where I can select from a list of UEFI boot devices. The options are "ubuntu" or something that starts with "uefi rst".

So I downloaded ubuntu boot repair onto a usb, opened up the one-time boot settings menu, and selected the USB under UEFI boot device. When boot repair ran, it didn't have any suggested repairs, just this output:

```
[COLOR=#000000][FONT=Helvetica]boot-repair-4ppa203[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][20230303_2033][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]============================== Boot Info Summary ===============================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda: ___________________________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]    File system:       iso9660[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]    Boot sector type:  Unknown[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]    Boot sector info: [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]    Operating System:  [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]    Boot files:        /boot/grub/grub.cfg[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]================================ 0 OS detected =================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]================================ Host/Hardware =================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]CPU architecture: 64-bit[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Video: Intel Corporation from Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]===================================== UEFI =====================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]BIOS/UEFI firmware: 2.9.0 from Dell Inc.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]The firmware is EFI-compatible, and is set in EFI-mode for this live-session.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]SecureBoot disabled (confirmed by mokutil).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]BootCurrent: 0002[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Timeout: 2 seconds[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]BootOrder: 0001,0000,0002,0003[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot0000* UEFI RST KBG40ZPZ512G NVMe KIOXIA 512GB Z09101EIN032     PciRoot(0x0)/Pci(0xe,0x0)/NVMe(0x1,8C-E3-8E-04-01-80-3E-A2)/HD(1,GPT,a0c36d0a-7a70-4e67-93bb-afc8d1ae1082,0x800,0x5f000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot0001* ubuntu    HD(1,GPT,a0c36d0a-7a70-4e67-93bb-afc8d1ae1082,0x800,0x5f000)/File(\EFI\ubuntu\shimx64.efi)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot0002* UEFI Memorex USB Flash Drive 070008BDB8BD1224    PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/HD(2,MBR,0x2c534026,0x3c4,0x1340)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot0003* UEFI Memorex USB Flash Drive 070008BDB8BD1224 2    PciRoot(0x0)/Pci(0xd,0x0)/USB(1,0)/CDROM(1,0x3c4,0x4d00)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]============================= Drive/Partition Info =============================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disks info: ____________________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Partitions info (1/3): _________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Partitions info (2/3): _________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Partitions info (3/3): _________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]fdisk -l (filtered): ___________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk sda: 57.8 GiB, 62026416128 bytes, 121145344 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk identifier: 0x2c534026[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]      Boot Start     End Sectors  Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda1  *        0 1802239 1802240  880M  0 Empty[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda2         964    5891    4928  2.4M ef EFI (FAT-12/16/32)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram0: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram1: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram2: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram3: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram4: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram5: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram6: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Disk zram7: 982.9 MiB, 1030602752 bytes, 251612 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]parted -lm (filtered): _________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda:62.0GB:scsi:512:512:msdos:Memorex USB Flash Drive:;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]2:494kB:3017kB:2523kB:::esp;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Free space >10MiB: ______________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda: 2.88MiB:59153MiB:59150MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]blkid (filtered): ______________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sda    iso9660  2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#9500;&#9472;sda1 iso9660  2020-06-13-00-42-55-00               2c534026-01                          Boot-Repair-Disk 64bit [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#9492;&#9472;sda2 vfat     D055-8513                            2c534026-02                          Boot-Repair-Disk 64bit [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Mount points (filtered): _______________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]           Avail Use% Mounted on[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]/dev/sda        0 100% /cdrom[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Mount options (filtered): ______________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]====================== sda/boot/grub/grub.cfg (filtered) =======================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot-Repair-Disk session[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Boot-Repair-Disk session (failsafe)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]==================== sda: Location of files loaded by Grub =====================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]           GiB - GB             File                                 Fragment(s)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]            ?? = ??             boot/grub/grub.cfg                             1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]======================== Unknown MBRs/Boot Sectors/etc =========================[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Unknown BootLoader on sda[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Suggested repair: ______________________________________________________________[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]The default repair of the Boot-Repair utility would not act on the boot.[/FONT][/COLOR]
```

The first thing that jumps out at me is that it's not finding any operating systems :-kAny suggestions for next steps to take?

---

### Post by tea for one on 2023-03-03
The boot-repair report does not offer much useful information.
As you pointed out, no operating systems detected.

Boot0000* UEFI RST KBG40ZPZ512G NVMe KIOXIA 512GB Z09101EIN032
The line above is intriguing.
Can you access your UEFI firmware and see if Intel RST has been re-enabled after you downloaded Windows again?
Disable it, if you can.

Can you boot any OS?
If not, run the boot-repair report again with RST disabled?

Just guesswork at the moment - I hope you have recent backups?

---

### Post by oldfred on 2023-03-03
You are showing no internal drive at all, just the USB flash drive.

Does UEFI/BIOS show a drive?
You show no Windows UEFI boot entry in UEFI.
But do have an Ubuntu UEFI boot entry using a GUID for a partition an a drive that not seen.

Do you have good backups?
Some Windows installers just reinstall to existing partitions, but some may totally erase drive, restoring it to like new (or no other partitions for Linux).

---

