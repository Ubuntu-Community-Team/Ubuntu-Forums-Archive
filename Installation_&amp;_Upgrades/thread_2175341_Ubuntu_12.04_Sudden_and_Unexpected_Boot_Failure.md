---
title: "Ubuntu 12.04 Sudden and Unexpected Boot Failure"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by cdaver on 2013-09-18
Hello All,

This is my first post on this forum after using Ubuntu since Karmic. I have recently upgraded from Lucid 10.04 LTS to Precise 12.04 LTS.
The actual upgrade went well and I had a fully functioning system with no real issues except for a slight performance drop. Nautilus was laggy and hanged when accessing large directories. (10K + files).
During my efforts to troubleshoot this issue I have evidently caused a problem which is preventing me from booting into the system.  All I remember doing really is benchmarking using Disk Utility. I have not  changed any config. Finally I rebooted the system at which point it refused to boot up.
It keeps looping from Dell Boot screen to the Intel Raid Screen with the CTRL+I option and back again.
I do see a quick loading grub... before it restarts again.

Based on this I created a Boot Repair disk and used it to repair my system.

Here is the information before I made any changes, just the report:

[http://paste.ubuntu.com/6124965/](http://paste.ubuntu.com/6124965/)

Here is the info after changes:

[http://paste.ubuntu.com/6125039/](http://paste.ubuntu.com/6125039/)

Please help.

Cheers.

Hardware Info:
Intel Core 2 Duo 3GHz x 2 
X86-64
8GB Ram DDR3 1066 MHz
320 GB Seagate Barracuda 7200 with RAID0
Radeon HD 3450

---

### Post by cdaver on 2013-09-18
Just to add that using the Boot Repair recommended settings did not resolve my issues.
Please Help.

---

### Post by sudodus on 2013-09-19
Hi cdaver,

I could read only the first pastebin link. Maybe you can upload the information of the second one again.

Have you got any backup of the system, either the old one or the new one? If so, it might be easiest to start from there again.

The final option would be to save your /home directory to an external drive (and also save other personal directories) and reinstall. But it is worth trying to repair the system before you resort to the final option. I must admit that I have no experience of RAID. [COLOR=#ff0000]I hope someone else, who knows RAID, can help you.[/COLOR]

---

### Post by cdaver on 2013-09-19
Hello sudodus,

Thanks for the response. 
the paste.ubuntu.com link takes time since it is quite large. It took me a good min to load.

No Backup :( 
The main issue does seem to be partition + raid related and i think this got messed up further when i ran boot repair.
Not that Boot Repair is not a good tool, Only it has main the mapper drive the boot partition and sda and sdb say unpartitioned

---

### Post by cdaver on 2013-09-20
Hello All,

Please help me. I am struggling here.

From what I can tell the problem is a messed up MBR and partition tables.

I am using the ubuntu live cd with GPARTED and TESTDISK, I also have BOOTREPAIR.

GParted shows:

/dev/mapper/isw_djjefcjiff_main1       EXT4           285.90GiB    73.55    212.35Gib    boot
/dev/mapper/isw_djjefcjiff_main2       extended      12.11GiB     --         --    
|->/dev/mapper/isw_djjefcjiff_main5   linux-swap    12.11Gib     --         --
unallocated                                    unallocated   6.85GiB

Here is the problem...
dev/sda                                        unallocated    149.01GiB
dev/sdb                                        unallocated    149.01GiB
Red Exclamation mark that says "Cant have a partition outside the disk".



Output from TestDisk.

Disk /dev/sda - 160GB / 149 GiB - ST3160318AS
Disk /dev/sdb - 160GB / 149 GiB - ST3160318AS
Disk /dev/mapper/isw_djjefcjiff_main - 319GB / 298 GiB
Disk /dev/mapper/isw_djjefcjiff_main1 - 306GB / 285 GiB
Disk /dev/mapper/isw_djjefcjiff_main2 - 13GB / 12 GiB
Disk /dev/mapper/isw_djjefcjiff_main5 - 13GB / 12 GiB
Disk /dev/sr0 - 742 MB / 708 MiB (RO) - DVD-ROM
Disk /dev/dm-0 - 319 GB / 298 GiB
Disk /dev/dm-1 - 306 GB / 285 GiB
Disk /dev/dm-2 - 13 GB / 12 GiB
Disk /dev/dm-3 - 13 GB / 12 GiB


sudo fdisk -lu /dev/sda does not display anything.
sudo fdisk -lu /dev/sdb displays "does not contain valid partition table message"

F1 F1 F1. Please.

---

### Post by cdaver on 2013-10-28
Closing this Issue.

I could not recover from this and had to do a fresh install of 12.04.

For the record, Going from 10.10 to 12.04 without backup was a brilliantly retarded idea. IDK what I was thinking when i hit that button.

---

