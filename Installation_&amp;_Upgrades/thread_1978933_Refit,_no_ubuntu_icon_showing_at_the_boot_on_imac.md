---
title: "Refit, no ubuntu icon showing at the boot on imac"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by edgargdl on 2012-05-12
Hi All, 

I am really struggling with my ubuntu on my imac, there is no linux icon appearing but instead is a windows icon, even if i clicked is not opening linux..

here is the info of my partitions, am i doing something wrong?


*** Report for internal hard disk ***

Current GPT partition table:
# Start LBA End LBA Type
1 40 409639 EFI System (FAT)
2 409640 487956615 Mac OS X HFS+
3 487956616 489226151 Mac OS X Boot
4 489226152 889204667 Basic Data
5 889204668 929105058 Linux Swap

Current MBR partition table:
# A Start LBA End LBA Type
1 1 409639 ee EFI Protective
2 * 409640 487956615 af Mac OS X HFS+
3 487956616 489226151 ab Mac OS X Boot
4 489226152 889204667 83 Linux

MBR contents:
Boot Code: Unknown, but bootable

Partition at LBA 40:
Boot Code: None (Non-system disk message)
File System: FAT32
Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 2, type Mac OS X HFS+
Listed in MBR as partition 2, type af Mac OS X HFS+, active

Partition at LBA 487956616:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 3, type Mac OS X Boot
Listed in MBR as partition 3, type ab Mac OS X Boot

Partition at LBA 489226152:
Boot Code: None
File System: ext4
Listed in GPT as partition 4, type Basic Data
Listed in MBR as partition 4, type 83 Linux

Partition at LBA 889204668:
Boot Code: None
File System: Unknown
Listed in GPT as partition 5, type Linux Swap


** i am using refit by the way**

---

