---
title: "REinstalling Ubuntu wihtout data loss"
date: 2017-07-09
forum: Installation &amp; Upgrades
---

### Post by plopmon on 2017-07-09
I have currently dual booted Windows 10 and Ubuntu 16.04. now I just want to get rid of windows and want Ubuntu to take over my system (nothing of windows should be there. like I formatted my C: drive and merged with Ubuntu but boot entries of Windows are still there and by default PC boots into windows unless I go to F9 menu [boot options])

is there a way to reinstall Ubuntu without losing ANY OF MY PROGRAMS/DATA ??

here are my partitions:

NAME FSTYPE SIZE MOUNTPOINT LABEL
loop1 squashf 79.5M /snap/core/1689 
sr0 1024M 
loop2 squashf 4K /snap/anbox-installer/17 
loop0 squashf 79.5M /snap/core/2312 
sda 465.8G 
&#9500;&#9472;sda2 vfat 100M /boot/efi 
&#9500;&#9472;sda9 ext4 1M /media/jayant/65d2f87a-9de6-4ce7-8896-197ca9f8f 
&#9500;&#9472;sda7 ext4 267G / 
&#9500;&#9472;sda5 ext4 940M 
&#9500;&#9472;sda3 ext4 16M 
&#9500;&#9472;sda1 ntfs 450M Recovery
&#9500;&#9472;sda8 swap 5.9G [SWAP] 
&#9492;&#9472;sda6 ntfs 191.4G New Volume




if anyone is curious about New Volume well its my E: Drive in which my precious data is there. (help would be appreciated if anyone knows how to remove windows metdata from it without booting into windows. I don't care if data loss occurs in it. at least ill get something from it)


**EDIT 1**
i am providing more details of my partitions

Disk /dev/loop0: 79.5 MiB, 83349504 bytes, 162792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 79.5 MiB, 83349504 bytes, 162792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 03F2813D-0FA2-40B9-9B3D-3B7BC2C5E47E


```
Device         Start                End                Sectors             Size         Type
/dev/sda1   2048               923647          921600            450M       Windows recovery environment
/dev/sda2   923648           1128447       204800           100M        EFI System
/dev/sda3   128448           1161215       32768             16M           Microsoft reserved
/dev/sda5   573405184    575330303  1925120        940M         Windows recovery environment
/dev/sda6    575332240   976769071  401436832   191.4G      Microsoft basic data
/dev/sda7    1161216        561051647  559890432   267G         Linux filesystem
/dev/sda8    561051648   573405183  12353536      5.9G          Linux swap
/dev/sda9    976771072   976773119   2048               1M             Linux filesystem

```

Partition table entries are not in disk order.

---

### Post by kurt18947 on 2017-07-09
I'm not knowledgeable enough to offer advice on how to accomplish what you want though I'm sure it's possible.  What I would recommend is to back up any data you value first, I'd probably do two copies and make sure the copies are readable/re-storable.

---

### Post by ajgreeny on 2017-07-09
See Boot-Repair in my signature below and follow the instructions there to run the Boot-info-script. I suspect you  may have installed Ubuntu in BIOS  mode whilst Windows 10 is UEFI.

**Do not run a default repair at this stage**, just run the script and post back here the pastebin URL you are given; someone will be able to look at that and advise you where to go from here.

---

