---
title: "Installed from burned DVD, but won't show up"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by james149 on 2015-06-27
So I installed the latest LTS version of Ubuntu to a 100GB partition on my MacBook Pro, but after it restarted it won't show up.

These are the results from the partition inspector that came with rEFIt if it helps:


```
*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    766378327  Mac OS X HFS+
 3      766378328    767647863  Mac OS X Boot
 4      767649792    976773119  Basic Data


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    766378327  af  Mac OS X HFS+
 3      766378328    767647863  af  Mac OS X HFS+
 4      767649792    976773119  83  Linux


MBR contents:
 Boot Code: None


Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)


Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active


Partition at LBA 766378328:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type af  Mac OS X HFS+


Partition at LBA 767649792:
 Boot Code: None
 File System: ext2
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

```

EDIT: This is what the partition looks like on the Disk Utility app
[IMG]http://hfimages.com/i/HIgn1[/IMG]

---

