---
title: "No linux icon in rEFIt boot menu"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by Alinchicken6 on 2013-02-16
Hello,
I decided to dual boot Ubuntu alongside OS X a couple of days ago without success. I put in my Ubuntu DvD and the boot menu comes up looking exactly like the picture below but without the Linux icon which from what I understood is needed to boot into Linux. I have a partition set up for Ubuntu and according to rEFIt, they are in synch.

I'm not sure if this is needed, but here it is anyway. What I get from running the Partition Inspector:
```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640   1758222135  Mac OS X HFS+
 3     1758222136   1759491679  Mac OS X Boot
 4     1759491680   1942112255  Mac OS X HFS+
 5     1942374400   1953523711  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640   1758222135  af  Mac OS X HFS+
 3     1758222136   1759491679  ab  Mac OS X Boot
 4     1759491680   1942112255  af  Mac OS X HFS+

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 1758222136:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 1759491680:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 1942374400:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 5, type Basic Data
```

The DvD is brand new with an ubuntu-12.10-desktop-amd64.iso that I've verified at least 5 times.

I hope this is just a simple mistake on my part as my ISP is having a problem with the signal strength and it took me 4 hours to download Ubuntu.

Thanks in advance to anyone who can help me fix this.

---

