---
title: "Triple Booting on an MBP"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by Wilco on 2010-11-18
I'm trying to get a triple-boot setup working with rEFIt and OSX 10.6.5/Win7/Ubuntu 10.10.

I'm finally to a point where rEFIt shows a OS X, Windows, and Linux option but the Linux item boots up windows. I just finished booting the live CD and installing grub on the ubuntu partition, but rEFIt is *still* booting windows with the Linux menu entry (and no new entries have appeared since the GRUB reinstall).

Here's what the rEFIt partition inspector is currently showing - can anyone spot any problems?

*Note: Currently I have 5 partitions (OS X @ 60GB, Win @ 120 GB, Ubuntu (swap) @ 2 GB, Ubuntu @ 58 GB, and a general storage partition (formatted in OS X's HFS).*

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    117597143  Mac OS X HFS+
 3      117860352    352233471  Basic Data
 4      469683936    976510983  Mac OS X HFS+
 5      352233472    356466687  Linux Swap
 6      356466688    469682175  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    117597143  af  Mac OS X HFS+
 3 *    117860352    352233471  07  NTFS/HPFS
 4      469683936    976510983  af  Mac OS X HFS+

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 117860352:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 469683936:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 352233472:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 356466688:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 6, type Basic Data

```

---

### Post by drs305 on 2010-11-18
I can't offer much help about your partitioning since I've not used it. 

What might be happening is that if Grub2 can't boot a selection because the menu number/name is out of range it will boot the previous one (e.g. if you pick 10 and only have 5 entries, it will boot #5).

It could be that it can't boot Ubuntu so it drops down the next available, which in this case would be Windows. Just a guess. 

Posting the grub.cfg file or the contents of RESULTS.txt from the boot info script found [here]("http://bootinfoscript.sourceforge.net") may be useful to someone who understands your system.

---

