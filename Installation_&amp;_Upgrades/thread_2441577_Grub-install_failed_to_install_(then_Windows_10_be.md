---
title: "Grub-install failed to install (then Windows 10 becomes unbooteable)"
date: 2020-04-24
forum: Installation &amp; Upgrades
---

### Post by Random20240316 on 2020-04-24
[COLOR=#000000][FONT=Arial]Greetings.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have tried installing Ubuntu 20.04 on my Dell Lattitude 6440 with[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]Legacy Mode[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]UEFI Secure Boot OFF[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]UEFI Secure Boot ON[/FONT][/COLOR] 
[/LIST]

[COLOR=#000000][FONT=Arial]with:[/FONT][/COLOR]

[LIST]
[*][COLOR=#000000][FONT=Arial]65GiB of / home partition[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]8GiB of swap memory[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]250MiB EFI partition[/FONT][/COLOR] 
[/LIST]

[COLOR=#000000][FONT=Arial]And I still get the same error when the installer tries to install grub.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Unable to install GRUB in /dev/sda[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Executing `grub-install /dev/sda` failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This is a fatal error.

I'm afraid that this could happen if I ever tried to install other distros.

PICTURE
[/FONT][/COLOR][COLOR=#000000][FONT=Arial][https://i.stack.imgur.com/aUvlB.jpg](https://i.stack.imgur.com/aUvlB.jpg)
Not my laptop, but this is the message that appears when installing.

I have tried stopping the installer, use boot-repair and restart the installer and select the already created partitions, this actually works, the grub menu shows up when booting up. But there is no Internet connection and now Windows is unbooteable and I can't restore the BCD file,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I tried the fixbootmrc, fixbootrebuilbcd, steps but at one point, I restarted my laptop wondering if I could see something different, but now I couldn't even boot into the repair usb because the BCD file was now missing. I don't know how.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Now that I reinstalled Windows again, I made a BCD backup, but I'm also intrigued that, if I tried it again and ran into the same problem the BCD backup couldn't actually work, so I'm wondering if this backup could actually work and get me back into Windows.[/FONT][/COLOR]

[[COLOR=#000000][FONT=Arial]https://askubuntu.com/questions/459620/unable-to-install-grub-in-dev-sda-when-installing-grub[/FONT][/COLOR]]("https://askubuntu.com/questions/459620/unable-to-install-grub-in-dev-sda-when-installing-grub")
[COLOR=#000000][FONT=Arial]In this one, I don't know what "say no to automatically install to MBR of first hard drive and manually tell it /dev/sdb" means.[/FONT][/COLOR]

[[COLOR=#000000][FONT=Arial]https://ubuntuforums.org/showthread.php?t=2353288[/FONT][/COLOR]]("https://ubuntuforums.org/showthread.php?t=2353288")
[COLOR=#000000][FONT=Arial]This one explains that I have to type ```
sudo dosfsck -t -a -w /dev/nvme0n1p1
``` before install to get the "Install Ubuntu alongside Windows 10" option, and honestly I would prefer to have this option, but I don't have a NVME hard drive, I only have a SATA hard drive, and some outputs from the terminal tell me that I&#8217;m running on HDD Legacy Mode[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]And I don't know how to tell if my Windows 10 install is UEFI or BIOS, MBR or gpt partitioning. Even less how to set up the correct one to install. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Info[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo smartctl -i /dev/sda[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-26-generic] (local build)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]=== START OF INFORMATION SECTION ===[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Model Family: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Western Digital Black Mobile[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device Model: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]WDC WD3200LPLX-75ZNTT0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Serial Number:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]WXM1E7581WA1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]LU WWN Device Id: 5 0014ee 6b11de856[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Firmware Version: 02.01A02[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]User Capacity:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]320,072,933,376 bytes [320 GB][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector Sizes: [/FONT][/COLOR][COLOR=#000000][FONT=Arial]512 bytes logical, 4096 bytes physical[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Rotation Rate:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]7200 rpm[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Device is:    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]In smartctl database [for details use: -P show][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]ATA Version is:   ACS-2, ACS-3 T13/2161-D revision 3b[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Local Time is:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Fri Apr 24 22:58:27 2020 UTC[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Available - device has SMART capability.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]SMART support is: Enabled[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Legacy Boot on HDD[/FONT][/COLOR]


```

```
[COLOR=#000000][FONT=Arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk /dev/loop0: 1.93 GiB, 2049204224 bytes, 4002352 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Disk /dev/loop1: 27.9 MiB, 28405760 bytes, 55480 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Disk /dev/loop3: 240.82 MiB, 252493824 bytes, 493152 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]



[COLOR=#000000][FONT=Arial]Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Disk /dev/sda: 298.9 GiB, 320072933376 bytes, 625142448 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk model: WDC WD3200LPLX-7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 7EA8E3D0-8A05-40E7-866C-1C87005A6828[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Device   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Start   [/FONT][/COLOR][COLOR=#000000][FONT=Arial]End   Sectors   Size Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda1 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2048   1085439   1083392   529M Windows recovery environment[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda2  1085440   1290239[/FONT][/COLOR][COLOR=#000000][FONT=Arial]204800   100M EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda3  1290240   1323007 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]32768[/FONT][/COLOR][COLOR=#000000][FONT=Arial]16M Microsoft reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sda4  1323008 625141759 623818752 297.5G Microsoft basic data[/FONT][/COLOR]




[COLOR=#000000][FONT=Arial]Disk /dev/sdb: 7.23 GiB, 7759462400 bytes, 15155200 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk model: USB Flash Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Disk identifier: 0x00019b50[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Device [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Boot Start  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]End  Sectors  Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/dev/sdb1  * [/FONT][/COLOR][COLOR=#000000][FONT=Arial]2048 15155199 15153152  7.2G  c W95 FAT32 (LBA)[/FONT][/COLOR]


```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]Would appreciate any help.

---

### Post by yancek on 2020-04-24
Ubuntu has had a site online for the specific purpose of explaining dual booting UEFI with windows. It's been online for years and is at the link below.   Your fdisk output shows that you have an EFI install.  Most of the questions (if not all) should be answered on that page.  Also, you forgot to post the link to the output of the boot repair script which is the primary purpose of the software.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Random20240316 on 2020-04-24
Ok, I checked System Information on my Windows 10 and I saw that it's set to UEFI and installed as EFI mode. I don't know if it was set to BIOS or if it had a Legacy install before formatting but right now I have it set as UEFI/EFI.

Also, it probably had something to do with Rufus because right now, I just realized that the partition scheme was defaulted to MBR, and I checked that my Windows 10 partition has the GPT scheme, I'm right now burning the USB with the GPT partition scheme and UEFI as the target system. So I guess it's safe to go?

>  Also, you forgot to post the link to the output of the boot repair script which is the primary purpose of the software.

I no longer have the output, sorry. I can check and post more things if you need them

---

