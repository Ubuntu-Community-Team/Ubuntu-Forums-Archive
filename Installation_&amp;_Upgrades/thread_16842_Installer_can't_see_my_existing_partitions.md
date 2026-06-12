---
title: "Installer can't see my existing partitions"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by Guillaume on 2005-02-24
Hi,

I have a disk 40 Go partitionned like this : 
10 Go - NTFS WinXP
  6 Go - NTFS data
17 Go - FAT - data
and free space

When I launch the Ubuntu Install, the only proposition I have is to format the whole disk. It doesn't see my existing partitions !
What's wrong ? How can I install without having to erease everything ?

Thanx for your help.

---

### Post by p!=f on 2005-02-24
[QUOTE=Guillaume]Hi,

I have a disk 40 Go partitionned like this : 
10 Go - NTFS WinXP
  6 Go - NTFS data
17 Go - FAT - data
and free space

When I launch the Ubuntu Install, the only proposition I have is to format the whole disk. It doesn't see my existing partitions !
What's wrong ? How can I install without having to erease everything ?

Thanx for your help.[/QUOTE]
There should be an option to partition the disk manually. You may also ALT+F2 (+F3,...) to activate another console and type sudo cfdisk /dev/hda (or /dev/sda) to be sure your NTFS/FAT partitions are visible.

---

### Post by Guillaume on 2005-02-24
actually, I've deleted one data partition and the installer found my freespace and allowed me to install.
Thanx for your answer.

Next step : get the wlan working.

---

