---
title: "cannot boot 10.04 of 3.8TB hardware RAID"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by hansano on 2010-06-22
I am trying to install ubuntu 10.04 server edition (64-bit) on a hp proliant dl 185 G5 server. This server comes with a HP smart array p400 controller and I put six 750GB hard drives into it. All hard drives belong to the same array. The combined space shows up as 3.8TB Compaq array during the installation process.

The installation process finishes without problems, but on rebooting the system all I get is a black screen with a prompt. If I leave the installation USB stick in I get a grub rescue prompt and the message 'error: file not found'.

After googling I believe the problem is related to the >2TB disk space which requires the use of a gpt partition table. I didn't find a solution for this problem online. Many people had software RAIDs or were able to install the OS on a separate smaller disk. I would not easily be able to do this and therefore hope that somebody can help me this problem. I've never come across gpt before and ubuntu 10.04 is also new for me. 

I booted the server via USB stick and collected the following information: 

  'ls' at the grub-rescue prompt :
(hd0) (hd1) (hd1,3) (hd1,2) (hd1,1)



gparted output (GUI):

Partition, File System, Size, Used, Unused, Flags
unallocated, unallocated, 1.00 MiB, ---, ---, 
/dev/cciss/c0d0p1, unknown*, 1.00 MiB, ---, ---, bios_grub
/dev/cciss/c0d0p2, ext4, 3.40TiB, 55.39 GiB, 3.35 TiB, 
/dev/cciss/c0d0p3, linux-swap, 11.33 GiB, ---, ---

* unrecognised disk label



fdisk -l 

Warning: GPT (GUID Partition Table) detected on '/dev'cciss/c0d0'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/cciss/c0d0: 3750.6 GB, 3750612557824 bytes 
255 heads, 63 sectors/track, 455986 cylinders
Units = cylinders of 16065 * 512 = 8335280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifiert: 0x00000000

    Device Boot    Start    End        Blocks    Id    System
/dev/cciss/c0d0p1    1    267350    2147483647+    ee    GPT

Disk /dev/sda: 4059 MB, 4059561984 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Secotr size (logical/physical): 512 bytes / 512 bytes
Disk identifier: 0x0004bcec

[the usb-stick]
    Device Boot    Start    End        Blocks    Id     System
/dev/sda1 *        1    494    3964384+    c    W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
    phys=(492, 254, 63) logical=(493, 139, 30)


I was also able to mount a 3.7 TB large partition which contained a boot/grub directory with a initrd.img and vmlinuz entry.

I'm not really sure what's missing and where I would have to change something. The unrecognised label warning from gparted is suspicious, yet I don't really know out to change it. I would be really thankful if somebody could give me some advise how I could get this server going.

---

